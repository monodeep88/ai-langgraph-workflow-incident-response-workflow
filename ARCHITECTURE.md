# Architecture

            Selected architecture: Incident Response Workflow

            Template path: templates/langgraph-workflow/incident-response-workflow

            ## Pipeline

            User Request -> Architecture Selection -> Topic Selection -> AI Blueprint Generation -> Template Selection -> Code Customization -> Project Validation -> GitHub Repository Creation -> GitHub Push

            ## Specialist Agents

            - **Architecture Agent**: Define app boundaries, data flow, runtime stack, and integration points.
- **Backend Agent**: Design FastAPI modules, service contracts, validation, and error handling.
- **Frontend Agent**: Design React screens, state flow, controls, and user feedback states.
- **Database Agent**: Design persistence models, sample data, indexes, and audit records.
- **Testing Agent**: Define contract tests, smoke tests, and generated project validation.
- **DevOps Agent**: Define environment variables, Docker workflow, and repository packaging.
- **Reviewer Agent**: Review the generated plan for completeness, security, and portfolio quality.

            ## Validation

            The source is expected to pass pytest, frontend build, Docker Compose config, and Docker build before publication.
