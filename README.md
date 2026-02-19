# 🗂️ Bucket-to-PGVector Ingestion Workflow (n8n-based)

This workflow automates downloading files from a storage bucket, generating embeddings, and storing them in Postgres with PGVector for semantic search.

<img width="1215" height="619" alt="Screenshot 2026-02-19 141944" src="https://github.com/user-attachments/assets/326acc3b-d16c-42d3-93ba-8460050245cd" />


---

## 📌 Overview

When manually triggered, the workflow:

1. Searches a storage bucket
2. Iterates over returned files
3. Downloads each file
4. Loads and parses document content
5. Generates embeddings via Ollama
6. Stores documents + vectors in Postgres (PGVector)
7. Applies hardware cooldown control

---

## 🧩 Workflow Steps

### 1️⃣ Trigger
**When clicking “Execute workflow”**

Manual execution entry point.

---

### 2️⃣ Search a Bucket
- Retrieves items from a configured storage bucket
- Outputs file list (e.g., 65 items)

---

### 3️⃣ Loop Over Items
- Iterates through each file returned from the bucket
- Processes items individually

---

### 4️⃣ Download a File
- Downloads the current file
- Passes file content to the document loader

---

### 5️⃣ Default Data Loader
- Extracts and structures document content
- Prepares text for embedding

---

### 6️⃣ Embeddings (Ollama)
- Generates vector embeddings locally using Ollama
- Outputs embedding vectors for each document chunk

---

### 7️⃣ Postgres PGVector Store
- Stores:
  - Document content
  - Embedding vectors
- Enables semantic search and similarity queries

---

### 8️⃣ Hardware Cooldown
- Throttles or pauses execution
- Prevents hardware overload during batch processing

---

## 🚀 Use Case

- Build a semantic search index from files in cloud storage
- Prepare data for RAG (Retrieval-Augmented Generation)
- Batch ingest documents into a vector database

---

## ⚙️ Requirements

- Postgres with PGVector enabled
- Ollama running locally
- Configured storage bucket access
- Hardware cooldown settings tuned for your machine

---

## 📦 Result

A searchable vector database populated from bucket files, ready for:

- Similarity search
- AI retrieval pipelines
- Knowledge base indexing

---

# ⚠️ Important Note

> **This repository demonstrates an example of an existing workflow.**  
> It is not a one-size-fits-all solution.

Users are expected to:
- Modify infrastructure components
- Replace services as needed
- Adjust scaling logic
- Tune batch sizes and rate limits
- Swap embedding providers or storage backends

Adapt this workflow to match your environment, security requirements, and production standards.

---
