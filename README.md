# Coursera Multimodal Intelligence Platform (MIP)

## Individual Project Submission

This repository contains the complete Coursera Multimodal Intelligence Platform developed as a group project.

My primary contribution focused on the data and database layer of the system, including data collection and source validation, multimodal data structuring, embedding generation, Qdrant vector storage and ingestion, visual asset integration, and data validation.

---

## Project Overview

Coursera-MIP is an AI-powered curriculum analytics and multimodal diagnostic engine. It processes course videos, captions, slides, video frames, quizzes, and discussions into a unified retrieval system, synthesizes pedagogical friction diagnostics through LLM reasoning, and delivers a human-in-the-loop recommendation pipeline.

The system is designed not only to answer questions from course material, but also to identify learning friction, provide grounded evidence, and generate actionable curriculum recommendations.

---

## Tech Stack by Module

### Frontend (`frontend/`)
- **Core**: Next.js 16 (App Router), React 19, TypeScript
- **Styling & UI**: Tailwind CSS v4, Shadcn UI, Radix / Base UI, Lucide Icons
- **State & Data Fetching**: TanStack React Query v5, Axios
- **Visualization**: Recharts
- **Forms & Feedback**: React Hook Form, React Hot Toast

### Backend (`backend/`)
- **API & Runtime**: FastAPI, Uvicorn, Python 3.10+
- **RAG & Orchestration**: LangChain, FastMCP (Model Context Protocol)
- **Vector Search & Reranking**: Qdrant, BM25 (`rank-bm25`), Cohere Rerank
- **LLM Reasoning & Output**: Groq, Instructor, Pydantic v2
- **Embeddings**: Sentence Transformers, Hugging Face Hub
- **Persistence**: Supabase (PostgreSQL)

### Database & Pipeline (`database/`)
- **Media Ingestion & Parsing**: OpenCV (video frames), PyMuPDF (slides & transcripts), WebVTT (captions)
- **Multimodal AI**: Google Gemini API (`google-genai`) for visual slide & frame analysis
- **Vector Ingestion**: Qdrant Client, Sentence Transformers (768-dim embeddings)
- **Relational Storage & Views**: Supabase (PostgreSQL schemas, views, and RLS policies)
- **Data Processing**: Pandas, NumPy, Pydantic

---

## Repository Structure

```text
coursera-mip/
├── backend/    # FastAPI server, RAG retrieval & synthesis pipeline, MCP server
├── database/   # Multimodal extraction, ingestion pipelines, and Supabase SQL
└── frontend/   # Next.js web application, diagnostic dashboard, and chat interface
---

## My Contribution

My contribution to the project focused primarily on the data collection, multimodal processing, vector database, and data validation layers.

### Data Collection & Source Validation
- Collected and validated course materials from MIT OpenCourseWare.
- Worked with raw course assets including videos, WebVTT captions, transcript PDFs, slide PDFs, quizzes, and discussion data.
- Structured the collected material for downstream processing and retrieval.

### Multimodal Data Structuring
- Processed and organized five content types:
  - Captions
  - Slides
  - Video Frames
  - Quizzes
  - Discussions
- Maintained shared identifiers such as `course_id`, `module_id`, and `lecture_id`.
- Established links between visual content, transcript chunks, quizzes, and discussions for cross-modal traceability.

### Embedding Generation
- Generated semantic embeddings using `BAAI/bge-base-en-v1.5`.
- Used 768-dimensional normalized embeddings with cosine similarity.
- Prepared searchable representations for the different content types.
- Used Gemini-generated textual analysis for visual content before embedding.

### Qdrant Vector Database & Ingestion
- Designed and populated the centralized Qdrant vector collection.
- Configured the collection with 768-dimensional vectors and cosine similarity.
- Integrated content metadata with vector records for retrieval and traceability.
- Implemented embedding validation, deterministic point IDs, batch ingestion, and record-level checks.
- Contributed to the final indexed dataset of 5,285 multimodal records.

### Visual Asset Integration
- Integrated slide and video-frame assets with the private Hugging Face visual dataset.
- Maintained references between Qdrant records and their corresponding visual assets.
- Validated asset paths, record mappings, and metadata.
- Kept visual assets separately stored while maintaining their references in the vector database.

### Data Validation & Traceability
- Validated processed records before vector ingestion.
- Verified embedding dimensions, record identifiers, and content-type consistency.
- Validated visual asset mappings and database records.
- Maintained traceability between retrieved evidence and the original course material.
