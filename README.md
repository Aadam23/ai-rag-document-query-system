# ai-rag-document-query-system

Built an end-to-end AI-powered document processing system that extracts, analyzes, and retrieves insights from unstructured documents using OCR, embeddings, and Retrieval-Augmented Generation (RAG).

This system automates document ingestion, transforms text into vector embeddings, and enables intelligent querying using semantic search.

## Features

- Semantic document search using vector embeddings
- Retrieval-Augmented Generation (RAG) workflow
- Context-aware question answering
- Supabase pgvector integration for similarity search
- Google Generative AI embeddings and LLM response generation
- n8n workflow orchestration for ingestion and retrieval pipelines

## Tech Stack

- n8n
- Google Generative AI API
- Supabase
- PostgreSQL
- pgvector
- JavaScript

## Architecture

This project is built as two connected n8n workflows:
### 1. Ingestion Workflow
Document Upload → OCR → Text Cleaning → Chunking → Embeddings Generation → Store Original File in AWS S3 → Store Text Chunks and Embeddings in Supabase

### 2. Query Workflow
User Question → Question Embedding → Vector Search in Supabase → Retrieve Relevant Chunks → LLM Response Generation
Together, these workflows form a Retrieval-Augmented Generation (RAG) system for intelligent document querying.

### Ingestion Pipeline
1. Document text is processed and chunked
2. Chunks are converted into embeddings using Google Generative AI
3. Content and embeddings are stored in Supabase with pgvector

### Query Pipeline
1. User submits a question through a webhook
2. The query is embedded using Google Generative AI
3. Supabase performs vector similarity search
4. Top matching chunks are combined into context
5. Gemini generates an answer using only the retrieved context

## Example Query

**Question:**  
What cloud skills does this document mention?

**Answer:**  
The document mentions experience with Azure, AWS, Kubernetes, CI/CD, and Infrastructure as Code using Terraform.

## Screenshots

1. Ingestion Workflow
<img width="1440" height="787" alt="Screenshot 2026-04-13 at 1 10 52 PM" src="https://github.com/user-attachments/assets/e045afff-200c-4239-8260-bc46269c852e" />

2. Query Pipeline
<img width="1440" height="900" alt="Screenshot 2026-04-14 at 11 28 09 PM" src="https://github.com/user-attachments/assets/6d0809ca-7024-42eb-a0c2-f8a3e1ff65f2" />

3. S3 Bucket
<img width="1440" height="900" alt="Screenshot 2026-04-14 at 11 28 33 PM" src="https://github.com/user-attachments/assets/9267771b-0c12-4f47-9dfd-1d601e4b213f" />

