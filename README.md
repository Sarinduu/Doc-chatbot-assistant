# doc-chatbot-assistant

An AI-powered chatbot that answers questions using the content of your uploaded **PDF** and **TXT** documents.

It combines **Google Gemini**, **FAISS**, **SentenceTransformers**, and **Gradio** to create a reliable, context-aware assistant that responds based solely on the information found in your documents.

---

## Features

* Accepts both PDF and TXT files
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

### 6. Launch the Chatbot

```bash
jupyter notebook
```

Open `doc-chatbot.ipynb` and run all cells.

---

## Notebook Step Overview

1. **Imports** – All required libraries are loaded and checked
2. **Environment Setup** – Loads `.env` variables for Gemini API key and content path
3. **Document Loading** – Reads and combines PDF and TXT files from a folder
4. **Text Chunking** – Splits long text into chunks for better embedding and retrieval
5. **Embedding & Indexing** – Creates sentence embeddings and indexes them with FAISS
6. **Semantic Search** – Retrieves chunks most relevant to the user's question
7. **Gemini Generation** – Sends chunks and question to Gemini model to generate an answer
8. **Gradio UI** – A chatbot interface is created to ask and receive answers interactively

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
