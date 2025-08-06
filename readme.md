# RAG Document Server API

This API provides a backend for a Retrieval-Augmented Generation (RAG) system, allowing you to upload documents, search their content, and ask questions using an LLM (Large Language Model) powered by the retrieved information.

---

## 🚀 Getting Started

The server initializes two core services on startup:
* **Elasticsearch**: Used as a fast, scalable search index for storing and retrieving document content. The API waits for Elasticsearch to be available before starting.
* **OpenAI LLM**: The `OpenAI` model is used for generating answers based on retrieved context. This requires the `OPENAI_API_KEY` environment variable to be set.

---

## 📋 API Endpoints

### Health Check

`GET /health`

This endpoint provides a detailed health status of the server and its dependencies. It's useful for monitoring the system's operational status.

**Example Response:**
```json
{
  "status": "healthy",
  "message": "RAG Document Server is running",
  "services": {
    "elasticsearch": {
      "available": true,
      "host": "http://elasticsearch:9200",
      "error": null,
      "index": "rag_docs"
    },
    "llm": {
      "available": true,
      "model": "gpt-3.5-turbo"
    }
  },
  "supported_file_types": {
    ".txt": "Plain text files",
    ".pdf": "PDF documents",
    ".docx": "Microsoft Word documents (new format)",
    ".doc": "Microsoft Word documents (legacy format)",
    ".pptx": "Microsoft PowerPoint presentations (new format)",
    ".ppt": "Microsoft PowerPoint presentations (legacy format)",
    ".json": "JSON files",
    ".py": "Python source code files"
  },
  "max_file_size_mb": 10
}

`GET /health`