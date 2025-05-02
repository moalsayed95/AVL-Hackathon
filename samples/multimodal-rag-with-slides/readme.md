# Multimodal RAG with presentation slides

This sample demonstrates a **multimodal Retrieval Augmented Generation (RAG)** solution, integrating **Azure AI Search**, **Azure OpenAI Service**, and **Microsoft Fabric**. The goal is to enrich responses with **textual and visual content** (e.g., images) extracted from ingested presentation slides, all managed within a unified search index.

## Key Components

- **Microsoft Fabric**: Stores documents and orchestrates ingestion, text and image extraction, embedding generation, indexing, and data cleanup with Fabric Notebooks
- **Azure OpenAI Service**: Analyses images, generates textual descriptions and generates semantic embeddings
- **Azure AI Search**: Hosts a unified search index for both embeddings and image descriptions

## Workflow

1. **Data Ingestion**  
    - Documents are uploaded to a Fabric Lakehouse.

2. **Content Extraction & Description Generation**  
   - Each slide is converted into an image.
   - For each image, a GPT-4o model generates a textual description describing the textual and visual content.

3. **Embedding Generation**  
   - An embedding is generated for each textual description using an embedding model from Azure OpenAI Service.

4. **Unified Multimodal Indexing**  
   The search index is extended to include multimodal data:
    - Textual description
    - Embedding
    - Base64 string of the original image

5. **Query & Retrieval**  
   When a user submits a query:
   - Rewrite the query.
   - Generate an embedding for the query using the same embedding model.
   - Perform retrieval using a hybrid search (keyword + vector search).
   - Results include both textual description and original image.

6. **Response Generation**  
   - Build a multimodal prompt that includes retrieved textual descriptions and images of slides.
   - GPT-4o generates a final enriched response, referencing both textual and visual elements.

## Guide

1. In your Fabric workspace, create a new lakehouse.
2. Upload documents into the Files section.
3. Import notebooks to workspace.
4. Run `01_document_processing_slides.ipynb` to generate textual descriptions and embeddings and ingest data into a search index in Azure AI Search
5. Run `02_rag_slides.ipynb` to run query the search index, retrieve relevant data and generate a response for a question.