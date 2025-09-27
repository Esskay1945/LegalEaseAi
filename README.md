# LegalEaseAi
LegalEase is an open-source AI assistant for Indian case law. Built with the Indian Kanoon API, FAISS, and Google Gemini, it helps users search, explore, and summarize court cases. The platform also supports secure login, profile management, contract drafting, and an AI-powered chatbot—all accessible through a clean, modern web dashboard.

⚖️ LegalEase – AI-Powered Legal Research Assistant

LegalEase is a full-stack AI-powered legal assistant designed for Indian case law research.
It integrates:
🔎 Indian Kanoon API for fetching fresh case law.
📚 HuggingFace Dataset (santoshtyss/indian_courts_cases) for semantic retrieval.
🧠 Google Gemini + FAISS for Retrieval-Augmented Generation (RAG).
🔐 SQLite + JWT authentication for secure user management.
📄 Contract Generator for drafting legal agreements.
💬 Chatbot Interface for interactive legal research.

🚀 Features
User Authentication
Signup / Login / JWT-based session management
Change password, profile management
Case Law Research
Semantic retrieval from pre-indexed dataset using FAISS
Indian Kanoon API for fresh case updates
AI-generated summaries of top cases with links to PDFs
LegalEase AI Chatbot
Query case law in plain English
Get concise AI summaries + suggested next steps
Contract Generator
Create and store custom legal contracts
Save contracts tied to logged-in user
Modern Frontend (Vanilla JS)
Dashboard with sidebar navigation
Research tab, Chat tab, Contract tab
Glassmorphism + gradient design

🛠️ Tech Stack

Frontend
HTML, CSS, JavaScript
Fetch API for backend communication

Backend
Node.js + Express
SQLite (via sqlite3 + sqlite)
bcrypt + JWT for authentication
API proxy to Python RAG service
RAG Service
Python + FastAPI
HuggingFace Datasets (Indian Courts)
FAISS Vector DB
LangChain + Google Gemini API
Indian Kanoon API integration

⚙️ Installation
1. Backend (Node.js) Setup
cd backend
npm install


Create .env in /backend with:
JWT_SECRET=supersecretkey


Run backend:
node server.js

Runs on: http://localhost:5000

3. RAG Service (Python) Setup
cd rag
pip install -r requirements.txt


Create .env in /rag with:

GOOGLE_API_KEY=your_gemini_api_key
INDIAN_KANOON_API_KEY=your_indian_kanoon_api_key
RAG_INDEX_DIR=./rag/faiss_index
DATASET_NAME=santoshtyss/indian_courts_cases
DATASET_SPLIT=train
MAX_ROWS=15000


Run RAG service:

uvicorn rag_service:app --reload --host 0.0.0.0 --port 8000

4. Frontend Setup

The frontend is served automatically by the Node.js backend.
Open: http://localhost:5000

📖 Usage

Signup/Login to access the dashboard.

Navigate to:
Case Research → Search for Indian case laws.
LegalEase AI → Chat with the AI for summaries.
Contract Generator → Create and save contracts.
Backend proxies all /api/chat requests to the Python RAG service.
RAG service fetches from FAISS + Indian Kanoon API + Gemini to give responses.

📂 Project Structure
legalease/
├── backend/          # Node.js backend (Express + SQLite)
│   ├── server.js
│   └── legalease.db
├── rag/              # Python RAG service
│   ├── rag_service.py
│   └── faiss_index/
├── public/           # Frontend (HTML, CSS, JS)
│   ├── index.html
│   ├── chat.html
│   ├── research.html
│   ├── contracts.html
│   └── script.js
└── README.md



🔮 Future Improvements

Add support for multi-lingual queries (Hindi, Tamil, etc.)
Add advanced filters (by court, year, bench, etc.)
Enable contract templates with AI drafting
Deploy on cloud (Render / Railway / Vercel + Fly.io for FastAPI)

📝 License

MIT License © 2025
