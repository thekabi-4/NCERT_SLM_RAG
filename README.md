# 🚀 SLM with RAG + TinyLlama (Colab Version)

[![Open In Colab]([[https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/<your-username>/<your-repo>/blob/main/notebooks/slm_rag_tinyllama_colab.ipynb](https://colab.research.google.com/drive/1GRP2_RNLLK6RkhZ6muXg5CLF03RzyoPb#scrollTo=XLP0-033S_Tw)](https://colab.research.google.com/drive/1GRP2_RNLLK6RkhZ6muXg5CLF03RzyoPb?usp=sharing))

A **Small Language Model (SLM)** built using **TinyLlama** + **Retrieval‑Augmented Generation (RAG)**. This project integrates **semantic search, grammar correction, and LLM inference** into a Colab‑ready pipeline for building **student‑friendly NCERT Q\&A assistants**.

---

## ✨ Key Highlights

* ⚡ **Lightweight LLM** → TinyLlama (1.1B) in GGUF format, optimized for Colab.
* 📚 **Retrieval‑Augmented Generation** → Answers are grounded in NCERT dataset context.
* 🔎 **Semantic Search** → FAISS + Sentence Transformers for efficient knowledge retrieval.
* 📝 **Spell + Grammar Correction** → SymSpell + LanguageTool ensure student‑ready responses.
* 🎯 **Answer Formatting** → Auto‑detects 1‑mark, 2‑mark, 5‑mark, or short answers.

---

## 🧭 How It Works

1. **Dataset ingestion** → Reads NCERT CSV (`Question`, `Answer`) and combines them.
2. **Embedding & Indexing** → Generates dense embeddings (`all-MiniLM-L6-v2`) and stores them in FAISS.
3. **Query Processing** → Student query is corrected for spelling/grammar and classified into answer format.
4. **Retrieval** → Top‑k relevant Q\&A pairs are fetched from FAISS.
5. **Prompt Construction** → Builds a structured prompt with retrieved context.
6. **Generation** → Passes prompt into TinyLlama (via `llama.cpp`) to produce the final answer.

---

## 📂 Repository Structure

```
├─ notebooks/
│  └─ slm_rag_tinyllama_colab.ipynb   # Main Colab notebook (full pipeline)
├─ models/                            # TinyLlama GGUF weights (downloaded in Colab)
├─ embeddings/                        # FAISS indices (auto‑generated)
├─ texts/                             # JSON text corpus (auto‑generated)
├─ requirements.txt                   # Dependencies
└─ README.md
```

---

## 🚀 Quickstart (Colab)

1. **Click the Colab badge** above to open the notebook.
2. **Mount Google Drive** and place NCERT dataset under `MyDrive/Ncert_dataset/`.
3. **Run all cells** to:

   * Build FAISS index from dataset
   * Correct spelling + grammar
   * Perform semantic search
   * Generate answers with TinyLlama

---

## 🔧 Technical Stack

* **Language Model** → [TinyLlama 1.1B Chat](https://huggingface.co/TinyLlama)
* **Embeddings** → [Sentence Transformers](https://www.sbert.net/) (`all-MiniLM-L6-v2`)
* **Vector Store** → FAISS
* **Spelling** → [SymSpell](https://github.com/wolfgarbe/SymSpell)
* **Grammar** → [LanguageTool](https://languagetool.org/)
* **Inference Engine** → [llama.cpp](https://github.com/ggerganov/llama.cpp)

---

## 🧩 Example Usage

```python
query = "Explain photosynthesis in 2 mark format"
run_rag_query(query)
```

**Output (sample):**

```
📚 Final Answer:
Photosynthesis is the process in which green plants use sunlight to make food.
- It converts carbon dioxide + water into glucose and oxygen.
(This answer is in 2-mark format.)
```

---

## 🩹 Troubleshooting

* **OOM in Colab** → Use 4‑bit GGUF model (already configured).
* **LanguageTool errors** → Ensure Java 17 is installed (handled in notebook).
* **Drive errors** → Re‑run `drive.mount()` in Colab.

---

## 📄 License

MIT
