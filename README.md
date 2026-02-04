# Medical PDF Chatbot (RAG)

A Retrieval-Augmented Generation (RAG) based **medical chatbot** that answers user questions strictly using the content of provided medical PDF documents.

PDFs are converted into embeddings and stored in Pinecone. At runtime, relevant PDF chunks are retrieved and passed to an LLM to generate concise, context-grounded answers.

⚠️ **Disclaimer:** This project is for educational and demonstration purposes only and does **not** provide medical advice or diagnoses.

---

## How It Works

1. Medical PDFs are loaded and split into text chunks  
2. Each chunk is embedded using a HuggingFace embedding model  
3. Embeddings are stored in a Pinecone vector database  
4. User questions are embedded and matched against stored vectors  
5. Retrieved context is passed to an LLM (`gpt-4o-mini`) to generate answers  

---

### Tech Stack

Backend: Flask

LLM: OpenAI gpt-4o-mini

Embeddings: HuggingFace Sentence Transformers

Vector Database: Pinecone

RAG Framework: LangChain

---

## How to Run Locally

### 1. Clone the repository
```bash
git clone https://github.com/chaitanyagandhi/medical-chatbot.git
cd medical-chatbot
```
### 2. Install dependencies
```bash
pip install -r requirements.txt
```
### 3. Set environment variables

Create a .env file in the project root:

```ini
OPENAI_API_KEY=your_openai_api_key
PINECONE_API_KEY=your_pinecone_api_key
```

### 4. Index PDFs (one-time step)

Place your medical PDF files inside a data/ directory and run:

```bash
python store_index.py
```

This step:

- Loads PDFs

- Splits them into chunks

- Generates embeddings

- Stores them in Pinecone

- You only need to run this again if PDFs change.

### 5. Run the application
```bash
python app.py
```

Open your browser and visit:

http://localhost:8080