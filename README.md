# Graph-Based RAG Query Engine

## Overview

The **Graph-Based RAG Query Engine** is a Retrieval-Augmented Generation (RAG) system that combines **Neo4j graph database, open-source semantic embedding models, and FAISS vector similarity search** to retrieve relevant system prompts based on user queries.

The primary objective is to store and manage system prompts in a centralized graph database and retrieve the most semantically relevant prompt using vector-based similarity search. This enables the system to provide contextually relevant instructions to an LLM based on the user's input.

## Architecture

The system integrates three major components:

1. **Neo4j – Prompt Storage**
   - Stores system prompts in a graph database.
   - Provides a structured and centralized approach to managing prompt information.
   - Acts as the primary storage layer for prompt retrieval.

2. **Open-Source Semantic Embedding Model**
   - Converts stored system prompts into numerical vector representations.
   - Generates embeddings that capture the semantic meaning of the prompts.
   - Converts incoming user queries into embeddings using the same embedding model.

3. **FAISS – Semantic Retrieval**
   - Uses Facebook AI Similarity Search (FAISS) for efficient vector similarity search.
   - Compares the user query embedding against stored prompt embeddings.
   - Retrieves the most semantically relevant system prompt based on vector similarity.

## Workflow

The query processing pipeline follows these steps:

1. **Prompt Storage:** System prompts required for the LLM are stored in the Neo4j database.
2. **Embedding Generation:** An open-source semantic embedding model converts the stored prompts into vector embeddings.
3. **User Query Processing:** The incoming user query is converted into an embedding using the same embedding model.
4. **Similarity Search:** FAISS performs vector similarity search to identify prompts that are semantically closest to the user query.
5. **Prompt Retrieval:** The most relevant system prompt is retrieved from the associated storage.
6. **LLM Context Preparation:** The retrieved system prompt can be used as contextual instructions for the language model to generate a relevant response.

## High-Level Architecture

```text
             User Query
                  |
                  v
       Semantic Embedding Model
                  |
                  v
           Query Embedding
                  |
                  v
          FAISS Vector Search
                  |
                  v
       Relevant Prompt Retrieval
                  |
                  v
          Neo4j Database
           (System Prompts)
                  |
                  v
       Retrieved System Prompt
                  |
                  v
          LLM Context / Input
                  |
                  v
          Generated Response
```

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core implementation |
| Neo4j | Graph database and system prompt storage |
| FAISS | Vector similarity search |
| Open-Source Embedding Model | Semantic embedding generation |
| RAG | Context-aware prompt retrieval |
| LLM | Response generation using retrieved instructions |

## Key Features

- **Graph Database Integration:** Uses Neo4j to organize and store system prompts.
- **Semantic Search:** Retrieves prompts based on contextual meaning rather than exact keyword matching.
- **Vector Similarity Retrieval:** Uses FAISS for efficient similarity-based retrieval.
- **Open-Source Embeddings:** Leverages open-source semantic embedding models.
- **Dynamic Query-Based Retrieval:** Identifies relevant system prompts based on incoming user queries.
- **Modular Architecture:** Separates prompt storage, embedding generation, and retrieval components.

## Project Objective

The project explores the integration of graph databases and vector search techniques to build a semantic prompt retrieval engine.

By combining Neo4j with FAISS and open-source embedding models, the system provides a foundation for retrieving contextually relevant system instructions and improving how LLMs receive task-specific context.

## Future Enhancements

- Implement graph relationship-based retrieval between related prompts.
- Introduce hybrid retrieval combining semantic and keyword-based search.
- Add reranking mechanisms to improve retrieval relevance.
- Integrate multiple LLM providers.
- Implement prompt versioning and metadata-based filtering.

---

**Project:** Graph-Based RAG Query Engine  
**Author:** Ritika Varpe
