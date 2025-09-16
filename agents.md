# Agents

## Agents

| Name | Description | Inputs | Outputs | Permissions |
|------|-------------|---------|----------|-------------|
| [App Tests Workflow](.github/workflows/app-tests.yaml) | Runs comprehensive tests across multiple OS and Python versions on push/PR. | Push/PR events, Python code changes | Test results, coverage reports | `contents: read` |
| [RAG Evaluation Workflow](.github/workflows/evaluate.yaml) | Evaluates RAG answer quality when `/evaluate` comment is posted on PRs. | PR comment `/evaluate`, Azure credentials | Evaluation metrics, performance reports | `id-token: write`, `contents: read`, `issues: write`, `pull-requests: write` |
| [Bicep Security Scan](.github/workflows/bicep-security-scan.yaml) | Scans infrastructure-as-code files for security vulnerabilities. | Bicep template files | Security scan report, alerts | `contents: read`, `security-events: write` |
| [Azure Deployment Workflow](.github/workflows/azure-dev.yaml) | Automated deployment to Azure using Azure Developer CLI. | Azure credentials, deployment triggers | Deployed application, infrastructure | `id-token: write`, `contents: read` |
| [Python Code Quality](.github/workflows/python-code-quality.yaml) | Enforces code quality standards using linting and formatting tools. | Python source code | Code quality reports, formatting fixes | `contents: read` |
| [RAG Evaluator](evals/evaluate.py) | Evaluates RAG system performance using custom metrics and ground truth data. | Evaluation config, ground truth dataset, chat responses | Evaluation scores, metrics report | File system read/write |
| [Safety Evaluator](evals/safety_evaluation.py) | Performs safety evaluation of AI responses for harmful content detection. | Chat responses, safety prompts | Safety assessment scores, risk analysis | File system read/write, AI model access |
| [Ground Truth Generator](evals/generate_ground_truth.py) | Generates ground truth data for RAG evaluation benchmarks. | Source documents, question templates | Ground truth Q&A pairs, evaluation dataset | File system read/write, AI model access |
| [Load Testing Agent](locustfile.py) | Simulates user load to test application performance and scalability. | Target endpoints, user scenarios | Performance metrics, response times, throughput | HTTP requests to target application |
| [Database Setup Script](scripts/setup_postgres_database.sh) | Initializes PostgreSQL database with required schema and extensions. | Database connection parameters, schema files | Configured database, pgvector extension | Database admin access |
| [Seed Data Script](scripts/setup_postgres_seeddata.sh) | Populates database with sample data for development and testing. | Database connection, sample data files | Populated database tables | Database write access |
| [Azure Role Setup](scripts/setup_postgres_azurerole.sh) | Configures Azure managed identity roles for PostgreSQL access. | Azure credentials, resource identifiers | Configured Azure roles and permissions | Azure resource management |
| [OpenAI Role Setup](scripts/setup_openai_role.sh) | Sets up Azure OpenAI service roles and permissions for the application. | Azure credentials, OpenAI resource details | Configured service roles | Azure AI services management |
| [Pre-commit Hooks](.pre-commit-config.yaml) | Automatically validates code quality, formatting, and standards before commits. | Staged code changes | Code quality checks, formatting fixes | Local file system access |
| [Azure Developer CLI](azure.yaml) | Orchestrates infrastructure provisioning and application deployment to Azure. | Azure subscription, service configuration | Deployed infrastructure, running application | Azure subscription management |
