# 💼 RAG Investment Evaluator

**RAG Investment Evaluator** is an AI-powered Streamlit app that automates the evaluation of startup investment memos using internal venture capital (VC) guidelines.

It uses **Retrieval-Augmented Generation (RAG)** by combining:
- MongoDB Atlas Vector Search for guideline retrieval,
- ChromaDB for memo storage,
- LangChain for orchestration,
- OpenAI GPT for intelligent evaluation.

---

## 🚀 Features

- 📥 Upload startup investment memos as PDFs  
- ✂️ Auto-summarize and store memos in ChromaDB  
- 📚 Retrieve relevant VC guidelines from MongoDB  
- 🧠 Evaluate memo fields using GPT (e.g., Funding, MRR, Team Info)  
- 🧾 Generate a structured PDF report  
- 💬 Interactive chatbot to query internal policies  

---

## 🧠 System Architecture

```plaintext
                         ┌────────────────────┐
                         │  Guidelines PDF    │
                         └────────┬───────────┘
                                  ↓
                    ┌────────────────────────────┐
                    │  Chunk + Embed + Store     │
                    │  (MongoDB Atlas V.S.)      │
                    └────────┬───────────────────┘
                             ↓
User Uploads Memo   ┌────────────────────────────┐
      PDF  ────────▶│ Summarize + Store in Chroma│
                   └────────┬────────────────────┘
                            ↓
         ┌────────────────────────────────────┐
         │ Evaluate Each Memo Field           │
         │ - Retrieve matching guidelines     │
         │ - Evaluate compliance using GPT    │
         └────────────────────────────────────┘
                            ↓
              ┌────────────────────────────┐
              │ Generate Evaluation Report │
              │      (Downloadable PDF)    │
              └────────────────────────────┘

+ Interactive Chatbot (MongoDB vector search + GPT)
```

---

## 📂 Project Structure

```bash
.
├── app.py                  # Streamlit main app
├── chat_handler.py         # Chatbot logic (guideline Q&A)
├── evaluate_fields.py      # Memo field evaluator (LLM)
├── load_guidelines.py      # Chunk & embed guidelines
├── summarize_memo.py       # Memo summarizer and ChromaDB loader
├── report_utils.py         # PDF report generator
├── key_param.py            # Your API keys (do NOT share)
├── requirements.txt        # Python dependencies
├── chroma_db/              # ChromaDB local storage
├── data/                   # Guideline and memo PDFs
└── README.md
```

---

## ⚙️ Setup Instructions

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/your-username/rag-investment-evaluator.git
cd rag-investment-evaluator
```

### 2️⃣ Install Dependencies

Make sure Python 3.9+ is installed.

```bash
pip install -r requirements.txt
```

### 3️⃣ Set Up Your API Keys

Create a `key_param.py` file:

```python
# key_param.py
MONGODB_URI = "your_mongodb_atlas_connection_string"
OPENAI_API_KEY = "your_openai_api_key"
```

---

## ▶️ Running the App

```bash
streamlit run app.py
```

The app will open in your browser.

---

## 🧪 How It Works

### 📝 Step 1: Load Guidelines (Run Once)

```bash
python load_guidelines.py
```

This loads and vectorizes internal VC guidelines into MongoDB Atlas.

---

### 📄 Step 2: Upload Memo PDF via App

- Upload your startup investment memo through the UI.
- The app will:
  - 🔍 Summarize the content  
  - 🧠 Extract key fields (Funding, Sector, MRR, etc.)  
  - 💾 Store content and metadata in ChromaDB  

---

### ✅ Step 3: Evaluate Memo Fields

- For each extracted field:
  - Retrieve relevant guidelines from MongoDB
  - Use GPT to evaluate compliance
- Download the final PDF evaluation report

---

### 💬 Step 4: Ask Policy Questions via Chatbot

- Ask anything like:
  - “What’s the funding limit?”
  - “What sectors are restricted?”
  - “What requires board approval?”
- The chatbot uses MongoDB Atlas Vector Search + GPT to respond

---

## 📌 Dependencies

```txt
streamlit
langchain
langchain-community
langchain-openai
langchain-groq
pymongo
PyMuPDF
fpdf
```

---



## 📬 Contact

Built by [Akhileswari Pemmanaboina](mailto:akhileswari712@gmail.com)

Feel free to fork, improve, and contribute!

> Empowering investors with AI-driven memo evaluation 🧠
