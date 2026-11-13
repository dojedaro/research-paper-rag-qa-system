# 📚 Research Paper Answer Bot  
**Production-Style Retrieval-Augmented Generation (RAG) System**  

---

## 🚀 Overview

This project is a **production-style Retrieval-Augmented Generation (RAG) system** designed to answer **technical research questions** directly from **academic AI research papers** with **strict source grounding**, **conversation memory**, and **quantitative evaluation**.

Unlike lightweight RAG demos, this system emphasizes **data cleanliness, retrieval rigor, explainability, and evaluation**, reflecting how real-world RAG systems are engineered, tested, and monitored.

---

## 🌐 Live Demo (Streamlit via ngrok)


## 🖼️ Application Screenshots

### User Login & Session Initialization
![User Login](screenshots/User%20Interface%20%26%20Log%20in.png)

### Technical Research Conversation (Example 1)
![Technical Chat 1](screenshots/Technical%20Chat%201.png)

### Technical Research Conversation (Example 2)
![Technical Chat 2](screenshots/Technical%20Chat%202.png)


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

---

## ▶️ Run it

```bash
pip install -r requirements.txt
unzip "Research Papers.zip" -d papers
jupyter notebook research_paper_rag_qa_system.ipynb
```

The notebook builds the index, writes the Streamlit app and launches it on port 8501. It asks for an
OpenAI API key and, to share a public link, an ngrok auth token (both read at runtime, never
stored in the repo). The retriever blends semantic and BM25 scores with `alpha = 0.7` toward the
semantic side.

## 🧰 Stack

Python, OpenAI API (GPT-4), rank-bm25, sentence embeddings, Streamlit, ngrok, pandas, Matplotlib.

## ⚠️ Limitations and next steps

- **The notebook is committed without outputs**, so the evaluation it implements (retrieval relevance,
  source coverage, latency, embedding benchmarks) has no saved numbers to show here. Rerunning it and
  committing a results table is the next step.
- The relevance and confidence scores are heuristics; a small set of questions with known answer
  passages would measure retrieval directly (hit rate and MRR on the five papers).
- `gpt-4` is an older model name; any current OpenAI chat model works in its place.

Part of a series of RAG projects: [strict PDF QA](https://github.com/dojedaro/strict-pdf-question-answering) ·
[PDF RAG + ReAct agent](https://github.com/dojedaro/pdf-rag-react-agent-langchain) ·
[policy QA with evaluation](https://github.com/dojedaro/openai-rag-policy-qa-evaluation) ·
[10-K retrieval evaluation](https://github.com/dojedaro/coca-cola-10k-retrieval-evaluation) ·
**research-paper RAG**

## License

MIT
