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
- 📚 Retrieve relevant internal VC guidelines from MongoDB
- 🧠 Evaluate memo fields using LLMs (e.g., Funding, MRR, Founder Info)
- 🧾 Generate a structured PDF report with compliance explanations
- 💬 Chatbot to answer policy/guideline questions from MongoDB

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

+ Interactive chatbot (MongoDB vector search + GPT)


#📂 Project Structure
```bash
.
├── app.py                  # Streamlit main app
├── chat_handler.py         # Chatbot logic (guideline Q&A)
├── evaluate_fields.py      # Memo field evaluator (LLM)
├── load_guidelines.py      # Chunk & embed guidelines
├── summarize_memo.py       # Memo summarizer and ChromaDB loader
├── report_utils.py         # PDF report generator
├── key_param.py            # Your API keys (do NOT share)
├── requirements.txt        # Required dependencies
├── chroma_db/              # Local ChromaDB storage for memos
├── data/                   # Store guideline/memo PDFs
└── README.md
```

#⚙️ Setup Instructions
```bash

#1️⃣ Clone the Repository
git clone https://github.com/your-username/rag-investment-evaluator.git
cd rag-investment-evaluator

#2️⃣ Install Dependencies
 Make sure you’re using Python 3.9+
pip install -r requirements.txt

#3️⃣ Set Up Your API Keys
 Create a key_param.py file:
```

# key_param.py
MONGODB_URI = "your_mongodb_atlas_connection_string"
OPENAI_API_KEY = "your_openai_key"

▶️ Running the App
```bash
streamlit run app.py
```
The app will launch in your browser.

#🧪 How It Works
```bash

📝 Step 1: Load Guidelines (Run Once)
python load_guidelines.py
```
This vectorizes and stores internal VC guidelines in MongoDB Atlas.


#📄 Step 2: Upload Memo PDF
1.Upload a startup investment memo via the app.
2.The app will:
  *Summarize the content
  *Extract key fields
  *Store in local ChromaDB


#✅ Step 3: Evaluate Memo Fields
1.For each field:
  *Retrieve matching guidelines
  *Use GPT to check compliance
2.View/download structured PDF report

#💬 Step 4: Ask Policy Questions via Chatbot
Ask questions like “What is the approval process ” or “What sectors are restricted?”
The chatbot searches MongoDB guidelines and answers using GPT



