# ⚖️ AI-Based Legal Reference and Case Retrieval System

This project is an **AI-powered system** for legal document reference and case retrieval. It helps users efficiently **search, retrieve, and analyze legal documents** by leveraging **LangChain**, **HuggingFace embeddings**, and **Pinecone vector databases** to build a **searchable knowledge base** from local files and external datasets.

---
## Project Structure

* **AI-Based-Legal-Reference-and-Case-Retrieval-System_September_2025/**
    * `Inputs/` - Input files (PDF, DOCX, TXT, HTML)
    * `Milestone-1/` - First milestone scripts
        * `Outputs/` - Generated outputs from Milestone-1
        * `task1.py` - Chunk local files into segments
        * `task2.py` - Process HuggingFace IPC dataset
        * `task3.py` - Generate embeddings for all chunks
    * `Milestone-2/` - Second milestone scripts
        * `task4.py` - Perform CRUD operations on Pinecone
        * `task5.py` - Run full pipeline (local + HuggingFace → Pinecone)
        * `task6.py` - Retrieve/search documents from Pinecone index
        * `task7.py` - Implementing openai gpt-3.5-turbo model
        * `task8.py` - Interactive Legal RAG Chatbot
        * `legal_system_template.py` - System prompt template for RAG chain
    * `Milestone-3/` - Third milestone: Full-stack application
        * `app.py` - Main Streamlit application entry point
        * `auth_pages.py` - UI components for auth pages (sign in/up)
        * `auth_utils.py` - Backend logic for user authentication & DB
        * `legal_chat_bot.py` - Core RAG chain implementation
        * `chatbot_system_template.py` - Detailed system prompt for the chatbot
        * `datasets_utils.py` - Script to ingest documents into Pinecone
        * `users.db` - SQLite database for users and chats
        * `bg.jpg` - Background image for UI
    * `config.py` - Loads API keys from .env (safe to push)
    * `.env` - Pinecone API key (should NOT be pushed)
    * `requirements.txt` - Python dependencies
    * `README.md` - Project documentation

---
## Setup Instructions

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/Springboard-Internship-2025/AI-Based-Legal-Reference-and-Case-Retrieval-System_September_2025.git](https://github.com/Springboard-Internship-2025/AI-Based-Legal-Reference-and-Case-Retrieval-System_September_2025.git)
    cd AI-Based-Legal-Reference-and-Case-Retrieval-System_September_2025
    ```
2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
3.  **Create a `.env` file** in the root directory with your API keys:
    ```
    PINECONE_API_KEY="YOUR_API_KEY"
    OPENAI_API_KEY="YOUR_API_KEY"
    ```
4.  **Verify configuration** in `config.py`:
    ```python
    import os
    from dotenv import load_dotenv

    BASE_DIR = os.path.dirname(__file__)
    load_dotenv(os.path.join(BASE_DIR, ".env"))

    PINECONE_API_KEY = os.getenv("PINECONE_API_KEY")
    OPENAI_API_KEY = os.getenv("OPENAI_API_KEY")
    ```

---
## Usage

### Milestone 1: Local & HuggingFace Data Processing

* `task1.py` — Chunk local legal files into manageable segments
* `task2.py` — Process HuggingFace IPC dataset
* `task3.py` — Generate embeddings for all chunks

### Milestone 2: Pinecone Integration

* `task4.py` — Perform CRUD operations on Pinecone vector database
* `task5.py` — Run the full pipeline: load data → generate embeddings → push to Pinecone
* `task6.py` — Retrieve/search documents from Pinecone index using queries
* `task7.py` — Implementing openai gpt-3.5-turbo model
* `task8.py` — Interactive Legal RAG Chatbot.
* `legal-system-template` — System prompt template for RAG chain

### Milestone 3: Full-Stack Streamlit Application

This milestone transforms the project into a complete web application with user management and persistent chat history.

* **`app.py`**: This is the main entry point to run the entire application. It handles page routing between the sign-in, sign-up, profile, and chatbot pages.
* **`auth_pages.py` / `auth_utils.py`**: These files provide a full authentication system. Users can sign up, sign in, and edit their profiles. User data, sessions, and chat history are stored in a SQLite database (`users.db`).
* **`legal_chat_bot.py`**: Creates the conversational RAG chain that powers the chatbot, using a system template, chat history, and retrieved documents to generate answers.
* **`datasets_utils.py`**: A utility script to process local files (PDF, DOCX, TXT) and store them as embeddings in the Pinecone vector database. This should be run once to populate the knowledge base.

#### How to Run Milestone 3:

1.  **Populate the knowledge base** by placing your legal documents in the `Inputs/` folder and running the script:
    ```bash
    python Milestone-3/datasets_utils.py
    ```
2.  **Launch the application**:
    ```bash
    streamlit run Milestone-3/app.py
    ```

---
## Dependencies

* langchain
* pinecone-client
* transformers
* datasets
* python-dotenv
* streamlit
* langchain-openai
* langchain-pinecone
* sentence-transformers
* pypdf
* docx2txt
* unstructured

---
## .gitignore Recommendation

```gitignore
# Python cache and artifacts
__pycache__/
*.pyc
*.pyo
*.pyd
*.egg-info/
*.swp

# Environment and virtual environments
.env
venv/
.venv/
*.venv/

# IDE and editor settings
.vscode/
.idea/
*.iml

# Project outputs and logs
Milestone-1/Outputs/
*.log

# Databases
users.db

# Streamlit and cache
.streamlit/
.cache/

# OS specific files
.DS_Store
Thumbs.db
```
This .gitignore ensures sensitive data like your API keys and unnecessary files are not pushed to GitHub.
