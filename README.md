# Incident Response Workflow

    ## Project Overview

    Incident Response Workflow is a complete full-stack AI project for **LangGraph workflow** at **Intermediate** difficulty. It includes a FastAPI backend, a React frontend, sample documents, vector search with ChromaDB support, source citations, timeline logs, structured run storage, Docker files, and tests.

    Incident Response is a critical process for organizations to respond to and manage incidents, minimizing their impact and ensuring business continuity.

    Difficulty controls project complexity, architecture depth, AI model selection, and how advanced the generated codebase is.

    - Architecture depth: FastAPI + React, ChromaDB vector search, better API structure, basic error handling
    - Selected architecture: Incident Response Workflow
    - Template path: templates/langgraph-workflow/incident-response-workflow
    - Generated stack: FastAPI, React, ChromaDB-ready vector store, SQLAlchemy run logs
    - README style: practical local setup with API and UI examples

    ## Tech Stack

    - Backend: Python, FastAPI, Pydantic, SQLAlchemy
    - AI/RAG: LangChain-ready prompt layer, ChromaDB vector storage, local deterministic fallback model
    - Workflow: LangGraph state-machine style flow
    - Frontend: React and Vite
    - Database: SQLite by default, PostgreSQL through Docker Compose
    - Testing: pytest
    - Difficulty: Intermediate

    ## Generation Method

    This project was generated with a template-based architecture engine. AI is used only for the blueprint, domain customization, sample data, prompts, and documentation. The codebase is produced from tested FastAPI/React/Docker templates rather than raw LLM source output.

    ## Folder Structure

    ```text
    ai-langgraph-workflow-incident-response-workflow/
      backend/
        app/
          main.py
          config.py
          db.py
          schemas.py
          data/sample_docs/
          services/
            text.py
            vector_store.py
            llm.py
            tools.py
            pipeline.py
        tests/
          test_project_contract.py
        requirements.txt
        Dockerfile
      frontend/
        src/
          App.jsx
          main.jsx
          styles.css
        package.json
        Dockerfile
      docker-compose.yml
      .env.example
      README.md
    ```

    ## Environment Variables

    ```env
    OPENAI_API_KEY=
    OPENAI_MODEL=gpt-4o-mini
    DATABASE_URL=sqlite:///./app.db
    ALLOWED_ORIGINS=http://localhost:5173,http://localhost:3000
    VITE_API_URL=http://localhost:8000
    ```

    The app runs without an OpenAI key by using a deterministic local answer model. Add `OPENAI_API_KEY` to use LangChain with OpenAI.

    ## Installation

    ```bash
    cd backend
    python -m venv .venv
    .venv\Scripts\activate
    pip install -r requirements.txt
    ```

    ```bash
    cd ../frontend
    npm install
    ```

    ## Run Backend

    ```bash
    cd backend
    uvicorn app.main:app --reload --port 8000
    ```

    ## Run Frontend

    ```bash
    cd frontend
    npm run dev
    ```

    ## Run With Docker

    ```bash
    docker compose up --build
    ```

    ## Example API Request

    ```bash
    curl -X POST http://localhost:8000/api/ask ^
      -H "Content-Type: application/json" ^
      -d "{\"question\": \"What is the refund policy?\"}"
    ```

    ## Example User Question

    ```text
    What should I do if a customer asks for a refund without an order id?
    ```

    ## Expected Output

    The API returns:

    - `answer`: a grounded answer generated from retrieved context
    - `sources`: cited document chunks with similarity scores
    - `steps`: planner, retriever, reasoning, tool-call, and final-answer timeline logs
    - `project_type`: `LangGraph workflow`

    ## How The RAG/Agent Flow Works

    LangGraph state machine with plan, retrieve, reason, tool, and final nodes.

    ## Project Planner Agent Workflow

    User -> React Dashboard -> FastAPI -> Project Planner Agent -> Specialist Agents -> Generated Project -> Auto Testing -> GitHub Repository Creation -> Push Code -> Return GitHub URL

    - **Architecture Agent**: Define app boundaries, data flow, runtime stack, and integration points. Outputs: Use a message broker (e.g., RabbitMQ) for communication between services.; Implement a database (e.g., PostgreSQL) for storing incident data.; Use a caching layer (e.g., Redis) for improving performance..
- **Backend Agent**: Design FastAPI modules, service contracts, validation, and error handling. Outputs: incident_management: Handles incident creation, assignment, and tracking.; communication: Manages communication with stakeholders, including email and SMS notifications.; reporting: Generates reports on incident status, impact, and resolution..
- **Frontend Agent**: Design React screens, state flow, controls, and user feedback states. Outputs: incident_dashboard: Displays incident status, assignment, and tracking information.; communication_panel: Allows team members to communicate with stakeholders.; reporting_tool: Provides reports on incident status, impact, and resolution..
- **Database Agent**: Design persistence models, sample data, indexes, and audit records. Outputs: Run history; Source document metadata; Generated workflow audit records.
- **Testing Agent**: Define contract tests, smoke tests, and generated project validation. Outputs: Use a combination of unit testing, integration testing, and end-to-end testing to ensure the workflow is functioning correctly..
- **DevOps Agent**: Define environment variables, Docker workflow, and repository packaging. Outputs: Docker-ready project; Environment sample file; GitHub repository upload.
- **Reviewer Agent**: Review the generated plan for completeness, security, and portfolio quality. Outputs: incident_creation: Create a new incident and assign it to a team member.; incident_assignment: Assign the incident to a team member and notify stakeholders.; incident_tracking: Track the status of the incident and update stakeholders accordingly..

    ## AI-Customized Domain Workflow

    - incident_creation: Create a new incident and assign it to a team member.
- incident_assignment: Assign the incident to a team member and notify stakeholders.
- incident_tracking: Track the status of the incident and update stakeholders accordingly.

    ## Business Rules

    - Incidents must be assigned to a team member within 30 minutes of creation.
- Team members must update the incident status every 2 hours.
- Stakeholders must be notified of incident updates within 1 hour.

    1. The backend loads sample documents from `backend/app/data/sample_docs`.
    2. Documents are split into chunks.
    3. Chunks are embedded and stored in ChromaDB when available, with a local fallback for development.
    4. User questions are matched against relevant chunks.
    5. Agent-specific steps run: planner, retriever, tool call, reasoning, reviewer, or graph nodes.
    6. The final answer is returned with source citations and a timeline.

    ## Testing

    ```bash
    cd backend
    pytest
    ```

    ## Validation Gates Before GitHub Push

    The SaaS validates generated projects before creating and pushing the GitHub repository:

    - `pytest`
    - `npm install`
    - `npm run build`
    - `docker compose config`
    - `docker compose build`
