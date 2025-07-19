# RAG Agent with Gemini and PDF Knowledge Base

This project demonstrates a Retrieval-Augmented Generation (RAG) agent using the Phi framework, Gemini model, and a PostgreSQL-backed vector database for efficient knowledge retrieval from PDF documents. Additionally, it integrates the DuckDuckGo search tool for web-based queries.

## Features
- **Retrieval-Augmented Generation (RAG)**: Fetches relevant information from stored PDFs and external sources.
- **Gemini Model Integration**: Uses `gemini-2.0-flash-exp` for generating responses.
- **PostgreSQL with pgvector**: Stores and retrieves vectorized document embeddings.
- **DuckDuckGo Search**: Enables web search capability for real-time information retrieval.
- **Agentic RAG**: The agent can intelligently search knowledge bases and maintain chat history.

## Installation

Ensure you have Python installed and set up a PostgreSQL database with `pgvector` enabled.

1. Clone the repository:
   ```sh
   git clone <repository-url>
   cd <repository-name>
   ```

2. Install dependencies:
   ```sh
   pip install phi psycopg2
   ```

3. Set up PostgreSQL and configure the database URL:
   ```sh
   export DATABASE_URL="postgresql+psycopg://ai:ai@localhost:5532/ai"
   ```

## Usage

### Load PDF Knowledge Base
Ensure your PDF files are stored in the `files` directory. Then, initialize and load them into the vector database:

```python
knowledge_base = PDFKnowledgeBase(path="files", vector_db=PgVector(...))
knowledge_base.load(upsert=True)  # Run this only once
```

### Initialize RAG Agent

```python
rag_agent = Agent(model=Gemini(id="gemini-2.0-flash-exp"), knowledge=knowledge_base, tools=[DuckDuckGo], ...)
```

### Run the Agent

```python
rag_agent.print_response("Show some information about Huawei", stream=True)
```
**Note: You need to set GOOGLE_API_KEY as environmental variable

## Demo
For a complete demonstration, refer to the provided Jupyter Notebook in the repository.

## Configuration
Modify the `db_url` variable to point to your PostgreSQL instance. Ensure `pgvector` is installed and enabled in your database.

## License
This project is licensed under the MIT License. See the `LICENSE` file for more details.

## Contributions
Feel free to fork the repository, submit pull requests, or report issues.

---
This setup enables a robust AI-powered knowledge retrieval system for interacting with PDFs and external sources efficiently.

