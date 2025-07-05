#  📚 Clustering-Based Summarization of Long Books (LangChain + Gemini)

This Colab notebook performs extractive + abstractive summarization of long books or PDFs by clustering semantically similar passages and summarizing the most representative ones using Google Gemini.

It’s particularly effective for books too long to fit into a single LLM context window.
---

### 🚀 Project Overview
Approach:
This pipeline follows a Map-Reduce style summarization using:

Gemini Embeddings: to embed chunks meaningfully

Clustering (KMeans): to group semantically similar chunks

t-SNE Visualization: to interpret cluster structure

LangChain Summarization Chain: to generate summaries

ROUGE, BLEU, METEOR, BERTScore, Cosine Similarity: to evaluate summaries

---

### ✨ Features

Load any book or long-form
Recursive character-based splitting with overlap
Convert chunks into meaningful vectors using Gemini Embeddings	embedding-001
Groups similar passages to find key topics using KMeans Clustering	
Picks crepresenattive passage from each cluster
📝 Map + Reduce Summarization	Summarizes representative passages → final full-book summary
📊 Evaluation Metrics	Uses ROUGE, BLEU, METEOR, and BERTScore to evaluate summary quality

---

###  Tech Stack

| Component         | Tool / Library                          |
|-------------------|------------------------------------------|
| LLM               | Gemini 1.5 Flash via LangChain           |
| PDF Processing    | Unstructured + Poppler + pdf2image       |
| OCR               | Tesseract (used within Unstructured)     |
| Embeddings        | GoogleGenerativeAIEmbeddings             |
| Vector Search     | DocArrayInMemorySearch                   |
| Text Splitting    | chunking_strategy="by_title" (Unstructured) |
| Image Captioning  | Gemini multimodal prompt via base64      |
| Summarization     | LangChain PromptTemplate + Gemini        |

---

### Example Use Case
"What is positional encoding?"

The assistant extracts relevant content from text and images (e.g., equations, graphs), providing an accurate summary using Gemini Flash.

---

### ⚙️ How to Use (Colab)
1. Open the notebook MMRAG.ipynb in Google Colab
2. Upload the research paper PDF
3. Add your Gemini API key
4. Enter your query in the space provided   
5. Run all cells in order.

---

### Setup Instructions (Local)
```bash

# Clone the repository
git clone https://github.com/Tipsy-12/Intelligent-Paper-Assistant.git
cd Intelligent-Paper-Assistant

# (Optional) Create and activate a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install Python dependencies
pip install -r requirements.txt

GOOGLE_API_KEY=your_gemini_api_key_here
LANGCHAIN_TRACING_V2=false
```

---

### ⚙️ System Dependencies
You’ll need the following tools installed on your system:

📦 Linux / Ubuntu / Codespaces:
```bash
sudo apt update && sudo apt install -y \
    poppler-utils \
    tesseract-ocr \
    libgl1
```
poppler-utils: for pdf2image to convert PDFs to images.

tesseract-ocr: for OCR capabilities in unstructured.

libgl1: required by opencv-python.

---

 ### 📁 Project Structure
```bash

├── main.py
├── config.py
├── requirements.txt
├── .env                 # Not committed (contains API keys)
├── utils/
│   ├── pdf_loader.py
│   ├── summarizer.py
│   ├── image_utils.py
│   ├── vector_store.py
├── app.py
```



