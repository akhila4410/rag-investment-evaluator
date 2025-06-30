# 💼 RAG Investment Evaluator

**RAG Investment Evaluator** is an AI-powered Streamlit application that automates the evaluation of startup investment memos using internal venture capital (VC) guidelines. It uses **Retrieval-Augmented Generation (RAG)** techniques with **MongoDB Atlas Vector Search**, **ChromaDB**, **LangChain**, and **OpenAI GPT**.

Built as a real-world application after completing the **RAG with MongoDB** course, this project demonstrates end-to-end RAG pipeline architecture, dynamic guideline retrieval, PDF summarization, LLM evaluation, and interactive chatbot support.

---

## 🚀 Features

- 📄 Upload startup investment memos as PDFs
- 📚 Automatically summarize and analyze memo content
- 📥 Retrieve relevant internal guidelines from MongoDB
- 🤖 Use LLM to evaluate each memo field (e.g., Funding Requested, MRR)
- 🧾 Generate a PDF evaluation report with explanations
- 💬 Chatbot to answer user questions using MongoDB Atlas Vector Search

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
         │ - Get relevant guidelines          │
         │ - Pass to LLM for judgment         │
         └────────────────────────────────────┘
                            ↓
              ┌────────────────────────────┐
              │ Generate Evaluation Report │
              │      (Downloadable PDF)    │
              └────────────────────────────┘

+ Integrated chatbot using MongoDB Vector Search


##🗂 Project Structure
.
├── app.py                  # Main Streamlit app
├── chat_handler.py         # Chatbot backend logic
├── evaluate_fields.py      # LLM field-level evaluator
├── load_guidelines.py      # Guideline chunking + embedding
├── summarize_memo.py       # Memo summarizer & ChromaDB loader
├── report_utils.py         # PDF report generator
├── key_param_example.py    # Example credentials (safe to share)
├── requirements.txt
├── .gitignore
└── README.md


🛠 Setup Instructions

🔁 1. Clone the repository
git clone https://github.com/your-username/rag-investment-evaluator.git
cd rag-investment-evaluator

📦 2. Install dependencies
pip install -r requirements.txt

🔐 3. Configure your keys
Create a file called key_param.py and paste your credentials:
# key_param.py
MONGODB_URI = "your_mongodb_atlas_connection_uri"
OPENAI_API_KEY = "your_openai_key"


▶️ Running the App
streamlit run app.py
The app will launch in your browser.
