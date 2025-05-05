# Azure AI Search Learning Path

This section focuses on leveraging Azure AI Search capabilities for vector search and semantic ranking to build powerful search applications.

## Learning Objectives

- Understand Azure AI Search basics including setup and configuration
- Implement vector search using HNSW (Hierarchical Navigable Small World) algorithm
- Configure and optimize semantic ranking for improved search results
- Compare different ranking methods (hybrid, vector, and semantic)
- Debug and analyze semantic ranker behavior

## Notebooks

### 1. Azure AI Search Basics (`azure_ai_search_basics.ipynb`)
- Setting up the Azure AI Search client
- Creating a simple vector search index
- Uploading documents with vector embeddings

### 2. Semantic Ranker Explained (`semantic-ranker.ipynb`)
- Creating a sample hotel index with vector search capabilities
- Configuring semantic ranker with different profiles
- Comparing semantic ranker results with traditional ranking
- Debugging semantic ranker interpretation of search results
- Analyzing captions and answers from semantic search

## Prerequisites

- Azure subscription with access to Azure OpenAI
- Azure AI Search service (basic tier or higher) with semantic ranker enabled
- Azure OpenAI deployment of text-embedding models

## Getting Started

1. Create a `.env` file based on `.env-sample` with your Azure Search and Azure OpenAI credentials
2. Set up a Python virtual environment using the provided requirements
3. Run the notebooks in sequence to understand the different concepts

## Key Concepts

- **Vector Search**: Uses vector embeddings to find semantically similar content
- **Semantic Ranker**: Re-ranks search results based on semantic understanding
- **Hybrid Search**: Combines traditional keyword search with vector search
- **Semantic Configuration**: Defines which fields are used for semantic ranking 