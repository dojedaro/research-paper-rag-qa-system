# 📚 Research Paper Answer Bot  
**Production-Style Retrieval-Augmented Generation (RAG) System**  

---

## 🚀 Overview

This project is a **production-style Retrieval-Augmented Generation (RAG) system** designed to answer **technical research questions** directly from **academic AI research papers** with **strict source grounding**, **conversation memory**, and **quantitative evaluation**.

Unlike lightweight RAG demos, this system emphasizes **data cleanliness, retrieval rigor, explainability, and evaluation**, reflecting how real-world RAG systems are engineered, tested, and monitored.

---

## 🌐 Live Demo (Streamlit via ngrok)

⚠️ **Deployment Note (Intentional Design Choice)**  
This application runs on **Streamlit locally** and is exposed publicly via **ngrok**.  
It is **not deployed on Streamlit Cloud**.

**Why this approach:**
- No API keys are stored in the repository
- Full control over OpenAI usage and cost
- Notebook ↔ app parity (reproducible development)
- Safe experimentation, debugging, and evaluation

> The public URL is generated dynamically at runtime when the app is launched.

---

## 🎯 Core Capabilities

### 🔍 Hybrid Retrieval Engine
- BM25 keyword retrieval
- Semantic similarity search
- Smart combination strategy + deduplication
- Top-K source selection with metadata and scores

### 🧹 Advanced Document Cleaning (Zero Contamination)
- Explicit removal of:
  - Legal boilerplate
  - Copyright/licensing text
  - Headers, footers, references sections
  - Non-AI or non-research content
- Ensures **research-only context**
- Reduces hallucinations caused by noisy PDF text

### 🤖 Answer Generation (GPT-4 + Fallback)
- Professional, technical response style
- Strict grounding in retrieved sources (citations by source)
- Automatic fallback mode when GPT-4 is unavailable
- Token usage + latency tracked per request

### 🧠 Conversational RAG
- Multi-user session handling
- Conversation memory window
- Follow-up question support (context-aware query enhancement)
- Lightweight user preference learning

### 📊 Evaluation & Analytics
- Retrieval relevance scoring
- Source coverage + diversity metrics
- Response latency monitoring
- Confidence estimation
- Embedding model benchmarking
- Notebook-based visualization dashboards

---

## 📄 Research Papers Indexed

The system answers questions **exclusively** from the following academic sources:

| Paper | Topic |
|------|------|
| attention_paper.pdf | Transformer & Attention Mechanisms |
| gpt4.pdf | GPT-4 Architecture |
| instructgpt.pdf | Instruction Tuning & RLHF |
| gemini_paper.pdf | Multimodal LLMs |
| mistral_paper.pdf | Open-Source Language Models |

No external web data is used.

---

## 🧩 System Architecture

```text
User Query
   ↓
Hybrid Retrieval (BM25 + Semantic)
   ↓
Clean Research Chunks (Noise-Free)
   ↓
GPT-4 / Professional Fallback Generator
   ↓
Answer + Sources + Confidence + Metrics


