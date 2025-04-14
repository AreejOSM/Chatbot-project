# SDA-bootcamp-project

Stage 4 - **RAG** Chatbot with Chat history

A RAG chatbot using Streamlit and FastAPI. At this stage, we will add the RAG function to the bot.
Other than creating normal chat, user can upload `pdf` file to the chatbot and ask questions specific to this document.

Under the hood, the system uses a vector store (Chroma) to retrieve the most relevant context from uploaded PDFs. This retrieval step enhances the chatbot’s ability to provide accurate, context-aware answers, bridging the gap between simple conversation and document-focused queries.

This enhancement integrates seamlessly with our existing setup—Streamlit for the user interface, FastAPI for business logic, and PostgreSQL for data storage—while laying the foundation for further expansion.

In this stage, we will create a **new** table called `advanced_chats` in the database using the following schema:
```
CREATE TABLE IF NOT EXISTS advanced_chats (
    id TEXT PRIMARY KEY,
    name TEXT NOT NULL,
    file_path TEXT NOT null,
    last_update TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    pdf_path TEXT,
    pdf_name TEXT,
    pdf_uuid TEXT
)
```
Step 1: Set Up Environment Variables
Store your OPENAI_API_KEY and Database Credentials in a .env file.

Your .env file should look like this:
```
OPENAI_API_KEY=
DB_NAME=
DB_USER=
DB_PASSWORD=
DB_HOST=
DB_PORT=
AZURE_STORAGE_SAS_URL=
AZURE_STORAGE_CONTAINER=

```
Step 2: Install Dependencies
To use ChromaDB, install it via pip. The necessary packages are listed in requirements.txt, so you can install everything by running:

pip install -r requirements.txt
Step 3: Start ChromaDB
To enable retrieval, we need to start ChromaDB. Use the following command to start the Chroma server:
```
chroma run --path /db_path
```
Replace /db_path with the directory where you want to store the data, e.g., chromadb.

Step 4: Start the Backend
Next, start the FastAPI backend:
```
uvicorn backend:app --reload --port 5000
```
Note: Compared to the last stage, we have added the --port 5000 parameter. Since ChromaDB uses port 8000 by default, this prevents a port conflict.

Step 5: Start the Streamlit App
Finally, run the Streamlit app:
```
streamlit run chatbot.py
```