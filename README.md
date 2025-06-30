# rag-investment-evaluator
An AI-powered RAG system that evaluates startup investment memos against internal VC guidelines using MongoDB Atlas Vector Search, ChromaDB, LangChain, and OpenAI.


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
🗂 Project Structure
bash
Copy
Edit
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
bash
Copy
Edit
git clone https://github.com/your-username/rag-investment-evaluator.git
cd rag-investment-evaluator
📦 2. Install dependencies
bash
Copy
Edit
pip install -r requirements.txt
🔐 3. Configure your keys
Create a file called key_param.py and paste your credentials:

python
Copy
Edit
# key_param.py
MONGODB_URI = "your_mongodb_atlas_connection_uri"
OPENAI_API_KEY = "your_openai_key"
This file is ignored by Git for safety.

▶️ Running the App
bash
Copy
Edit
streamlit run app.py
The app will launch in your browser.

🧪 Example Workflow
Step 1 – Load internal VC guidelines using load_guidelines.py

Step 2 – Upload a startup memo PDF in the UI

Step 3 – App will summarize and extract key fields

Step 4 – For each field (e.g., "Funding Requested"), relevant policy is fetched from MongoDB

Step 5 – An OpenAI LLM evaluates compliance

Step 6 – A clean PDF report is generated

Step 7 – Use the chatbot to query any policy/guideline

💡 Technologies Used
MongoDB Atlas Vector Search – for storing and retrieving guideline chunks

LangChain – for orchestrating document retrieval and LLM prompts

ChromaDB – to store memo summaries

OpenAI GPT – for field-level evaluation logic

Streamlit – for a clean web UI

FPDF – to generate downloadable reports

PyMuPDF – for extracting text from uploaded PDF memos

📷 Screenshots (Optional)
You can include UI screenshots or a GIF demo here if you want visual engagement on GitHub.

📄 Example Guidelines & Memo Fields
Example memo fields evaluated:

Funding Requested

Sector

MRR (Monthly Recurring Revenue)

ESG Compliance

Equity Offered

Use of Funds

Founder Background

Board Approval

Each field is:

Extracted from the memo

Matched to a relevant internal policy

Evaluated by an LLM

Added to the final evaluation report

🔐 Security Notes
All API keys (MongoDB, OpenAI) must be stored in key_param.py

Do not share this file or commit it to GitHub

📘 Learning Source
This project was built after completing:

✅ RAG with MongoDB Course
A hands-on certification program for building Retrieval-Augmented Generation systems with MongoDB Atlas.

📃 License
This project is open-sourced under the MIT License.

🤝 Acknowledgments
MongoDB & LangChain for incredible tooling

Streamlit for enabling rapid UI prototyping

OpenAI for LLM-powered reasoning

🌐 Author
Akhileswari Pemmanaboina
Computer Science Graduate | AI & Data Engineer
