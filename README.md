#  📚 Clustering-Based Summarization of Long Books (LangChain + Gemini)

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
| Vector Search     | DocArrayInMemorySearch                   |
| Clustering	| KMeans from scikit-learn |
| Dimensionality Reduction	| t-SNE (sklearn)      |
| Evaluation	| ROUGE, BLEU, METEOR, BERTScore, Cosine Similarity      |






