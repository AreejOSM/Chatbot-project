# SDA-bootcamp-project
**RAG** Chatbot with Chat history

A RAG chatbot using Streamlit and FastAPI. At this stage, we will add the RAG function to the bot.
Other than creating normal chat, user can upload `pdf` file to the chatbot and ask questions specific to this document.

Under the hood, the system uses a vector store (Chroma) to retrieve the most relevant context from uploaded PDFs. This retrieval step enhances the chatbot’s ability to provide accurate, context-aware answers, bridging the gap between simple conversation and document-focused queries.

This enhancement integrates seamlessly with our existing setup—Streamlit for the user interface, FastAPI for business logic, and PostgreSQL for data storage—while laying the foundation for further expansion.

##How to Get Started
Step 1: Set Up Environment Variables
Store your OPENAI_API_KEY, Database Credentials and Storage SAS token in a .env file.

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
Step 2: Start Sartup Script
```
chmod +x setup.sh
./setup.sh <PAT_token> <repo_url> <branch_name> <password>
```
