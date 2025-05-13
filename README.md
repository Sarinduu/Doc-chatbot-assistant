# doc-chatbot-assistant

An AI-powered chatbot built on the Retrieval-Augmented Generation (RAG) architecture. It allows users to ask natural language questions based on the content of their own **PDF** and **TXT** documents.

It combines **Google Gemini**, **FAISS**, **SentenceTransformers**, and **Gradio** to deliver reliable, context-aware answers grounded entirely in your uploaded files.

---

## Features

* Accepts both PDF and TXT files (TXT files are preferred for better answer quality)
* Extracts and splits documents into meaningful text chunks
* Embeds content using SentenceTransformers
* Retrieves relevant chunks using FAISS vector similarity search
* Generates answers using Google's Gemini model
* Simple and clean Gradio-based chatbot UI
* Logs questions and answers with timestamps

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/Sarinduu/Doc-chatbot-assistant.git
cd doc-chatbot-assistant
```

### 2. Create a Virtual Environment (Recommended)

```bash
python -m venv chatbot-env
source chatbot-env/bin/activate  # On Windows: chatbot-env\Scripts\activate
```

### 3. Create Your `.env` File

```bash
cp .env.example .env
```

Edit `.env` and set:

* Your Gemini API key
* Path to the folder with `.pdf` or `.txt` files. Default location: `source_materials`
* A custom document title (used in UI)

### 4. Install Requirements

```bash
pip install -r requirements.txt
```

### 5. Add Your Documents

Place your `.pdf` and `.txt` files in the folder specified in the `.env` (`source_materials/`). A placeholder file `content_placeholder.txt` is provided with sample data and questions. Remove it before use.

### 6. (Optional) Register Virtual Environment with Jupyter

If you are using a virtual environment, it's recommended to register it with Jupyter so you can run the notebook using that environment:

```bash
python -m ipykernel install --user --name=chatbot-env --display-name "ChatBot ENV"
```

### 7. Launch the Chatbot

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open the file `doc-chatbot.ipynb` from the interface. If you registered your virtual environment, make sure to select the **"ChatBot ENV"** kernel from the Kernel menu.

Then run all the cells in the notebook to start the chatbot interface.

---

## Notebook Step Overview

1. **Imports** – All required libraries are loaded and checked
2. **Environment Setup** – Loads `.env` variables for Gemini API key and content path
3. **Document Loading** – Reads and combines PDF and TXT files from a folder
4. **Text Chunking** – Splits long text into chunks for better embedding and retrieval
5. **Embedding & Indexing** – Creates sentence embeddings and indexes them with FAISS
6. **Semantic Search** – Retrieves chunks most relevant to the user's question
7. **Connect to Gemini Model** – Sets up the Google Gemini model using the google-genai client
8. **Answer Generation** – Sends the prompt (question + chunks) to Gemini and receives a context-aware response
9. **Gradio UI** – Builds an interactive chatbot interface for asking questions and displaying answers

---

## Tech Stack

* `gradio` – UI for the chatbot
* `sentence-transformers` – For embedding content
* `faiss` – Fast vector similarity search
* `google-genai` – Interface to Gemini model
* `PyMuPDF` – PDF text extraction
* `dotenv` – Secure management of API keys and paths

---

## Example Project Structure

```
doc-chatbot-assistant/
├── doc-chatbot.ipynb        # Main notebook with complete chatbot code
├── requirements.txt         # Required packages
├── .env.example             # Example env configuration
├── README.md                # This documentation
├── source_materials/        # Your PDF and TXT input folder
│   └── content_placeholder.txt
└── chatbot-env/             # (optional) Virtual environment
```

---

## License

MIT — Free to use and modify. Attribution is appreciated if this project helps you!

---
