#  📚 Semantic Clustering-Based Summarisation of Long Books

This Colab notebook performs extractive + abstractive summarization of long books or PDFs by clustering semantically similar passages and summarizing the most representative ones using Google Gemini.

It’s particularly effective for books too long to fit into a single LLM context window.
---

###  Tech Stack

| Component         | Tool / Library                          |
|-------------------|------------------------------------------|
| LLM               | Gemini 1.5 Flash via LangChain           |
| PDF Loading    | LangChain's PyPDFLoader / PyMuPDFLoader      |
| Text Splitting | LangChain's RecursiveCharacterTextSplitter   |   
| Embeddings        | GoogleGenerativeAIEmbeddings             |
| Clustering	| KMeans from scikit-learn |
| Dimensionality Reduction	| t-SNE (sklearn)      |
| Evaluation	| ROUGE, BLEU, METEOR, BERTScore, Cosine Similarity      |

---

### 📊 Evaluation Metrics 


| Metric               | Wikipedia Reference                    | AI-Generated Reference                |
|----------------------|----------------------------------------|---------------------------------------|
| 🔴 **ROUGE-1 (F1)**   | 0.1535 (P: 0.1100, R: 0.2537)           | 0.2635 (P: 0.2362, R: 0.2980)          |
| 🟠 **ROUGE-2 (F1)**   | 0.0376 (P: 0.0265, R: 0.0650)           | 0.0829 (P: 0.0713, R: 0.0992)          |
| 🟡 **ROUGE-L (F1)**   | 0.1354 (P: 0.0971, R: 0.2239)           | 0.2383 (P: 0.2136, R: 0.2694)          |
| 🔵 **BLEU**           | 0.0116                                 | 0.0186                                |
| 🟣 **METEOR**         | 0.222                                  | 0.2592                                |
| 🟢 **BERTScore (F1)** | 0.0217                                 | 0.1816                                |
| 🧠 **Cosine Similarity** | 0.8307                             | 0.9293                                |


---

### 🧠 Conclusions

- Our LLM-generated summary aligns closely with detailed, human-style references, achieving a **cosine similarity of 0.83**.
- Traditional lexical metrics (ROUGE, BLEU, etc.) **underestimate semantic match** when comparing summaries with differing granularity or phrasing because they rely on surface-level word overlap.
- **Embedding-based evaluation (Cosine Similarity)** provides a more reliable assessment of summary quality in long-document tasks.
- Our summary shows significantly stronger alignment with an **AI-generated reference** than with a brief Wikipedia-style summary.




