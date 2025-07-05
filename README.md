#  📚 Clustering-Based Summarization of Long Books

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

### Results

### 📊 Evaluation Metrics when the reference summary is taken from Wikipedia

| Metric               | Score                                  |
|----------------------|----------------------------------------|
| 🔴 **ROUGE-1 (F1)**   | 0.1535 (P: 0.1100, R: 0.2537)           |
| 🟠 **ROUGE-2 (F1)**   | 0.0376 (P: 0.0265, R: 0.0650)           |
| 🟡 **ROUGE-L (F1)**   | 0.1354 (P: 0.0971, R: 0.2239)           |
| 🔵 **BLEU**           | 0.0116                                 |
| 🟣 **METEOR**         | 0.222                                  |
| 🟢 **BERTScore (F1)** | 0.0217                                 |
| 🧠 **Cosine Similarity** | 0.8307                             |

### 📊 Evaluation Metrics when the reference summary is AI-generated

| Metric               | Score                                  |
|----------------------|----------------------------------------|
| 🔴 **ROUGE-1 (F1)**   | 0.2635 (P: 0.2362, R: 0.2980)           |
| 🟠 **ROUGE-2 (F1)**   | 0.0829 (P: 0.0713, R: 0.0992)           |
| 🟡 **ROUGE-L (F1)**   | 0.2383 (P: 0.2136, R: 0.2694)           |
| 🔵 **BLEU**           | 0.0186                                 |
| 🟣 **METEOR**         | 0.2592                                 |
| 🟢 **BERTScore (F1)** | 0.1816                                 |
| 🧠 **Cosine Similarity** | 0.9293






### Conclusions : 
1. Our LLM summary is factually and thematically solid — it closely matches the meaning of a rich, human-style reference.
2. Traditional metrics, such as ROUGE/BLEU, severely underrepresent this match because they rely on surface-level word overlap.
3. A better metric to evaluate the quality of a summary is Cosine Similarity between vector embeddings of the reference and generated summaries.
4. Our summary matches more with an AI-generated refernce summary (obviously).




