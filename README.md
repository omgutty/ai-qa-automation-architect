# AI QA Automation Architect Platform

An enterprise-grade multi-agent AI platform that transforms Jira requirements into structured test artifacts using Langflow, n8n, OpenRouter, and ChromaDB.

## Tech Stack

- Langflow
- n8n
- OpenRouter
- ChromaDB
- FastAPI
- Next.js
- Vercel

---

## Getting Started

### Prerequisites

- **Python 3.12** (managed via [uv](https://docs.astral.sh/uv/))
- **uv** installed globally

### Setup

```powershell
# Pin Python version and create virtual environment
uv python pin 3.12
uv venv

# Activate the virtual environment
.\.venv\Scripts\Activate.ps1

# Install Langflow
uv add langflow
```

> **Note:** If you get a `Multiple top-level packages discovered` build error, add `[tool.setuptools] packages = []` to `pyproject.toml`. This tells setuptools the root project is a container, not a Python package.

### Start Langflow

```powershell
# Start Langflow with default settings (http://localhost:7860)
uv run langflow run

# Start with custom port
uv run langflow run --port 7860

# Start with a specific .env file
uv run langflow run --env-file .env

# Start in development mode (includes beta features)
uv run langflow run --dev

# Start backend only (no frontend served)
uv run langflow run --backend-only

# Open browser automatically on start
uv run langflow run --open-browser
```

| Option | Default | Description |
|--------|---------|-------------|
| `--host` | `127.0.0.1` | Bind address |
| `--port` | `7860` | Listening port |
| `--workers` | `1` | Number of worker processes |
| `--env-file` | — | Path to `.env` file |
| `--log-level` | `info` | Logging level |
| `--open-browser` | `false` | Auto-open browser on start |
| `--backend-only` | `false` | Run backend without frontend |
| `--dev` | `false` | Development mode |

### Access the UI

Open [http://localhost:7860](http://localhost:7860) in your browser. From here you can create and manage flows using the visual editor.

### Langflow Flow Directory

All Langflow flow exports and definitions live in:

```
langflow/
├── exports/        # Import/export .json flow files
├── flows/          # Flow definitions
└── prompts/        # Langflow-specific prompt templates
```

---

## Project Structure

```
ai-qa-automation-architect/
│
├── backend/                    # FastAPI Python backend
│   └── app/
│       ├── agents/             # AI agent modules (stubs)
│       ├── api/                # API route handlers (stubs)
│       ├── models/             # Pydantic/DB models (stubs)
│       ├── prompts/            # Agent system prompts (.md)
│       ├── schemas/            # JSON data contracts
│       ├── services/           # Business logic layer (stubs)
│       └── utils/              # Utility functions (stubs)
│
├── frontend/                   # Next.js frontend (not yet scaffolded)
├── langflow/                   # Langflow flows, exports, prompts
│   ├── exports/
│   ├── flows/
│   └── prompts/
│
├── n8n/                        # n8n workflow JSON files
│   └── workflows/
│
├── rag/                        # RAG pipeline
│   ├── chromadb/               # ChromaDB vector store data
│   ├── ingestion/              # Document ingestion scripts
│   └── retrieval/              # Document retrieval/query scripts
│
├── docs/                       # Documentation
├── prompts/                    # Root-level prompt definitions
├── templates/                  # Markdown/HTML report templates
├── sample-data/                # Sample input/output data
│   ├── jira/
│   ├── output/
│   └── testcases/
│
├── output/                     # Generated artifacts
│   ├── json/
│   ├── markdown/
│   └── reports/
│
├── deployment/                 # Deployment configs (Docker, etc.)
├── .env                        # Environment variables
├── pyproject.toml              # Python project config
├── .python-version             # Python 3.12 pin
└── uv.lock                     # Dependency lock file
```

---

## Architecture

```
                        Next.js (Frontend)
                               │
                               ▼
                     FastAPI Backend (API Layer)
                               │
                    ┌──────────┴──────────┐
                    ▼                     ▼
                 n8n                  Langflow
          (Orchestration)      (AI Reasoning & RAG)
                    │                     │
                    └──────────┬──────────┘
                               ▼
                          OpenRouter LLM
                               │
                               ▼
                           ChromaDB
                               │
                               ▼
                        Markdown / HTML / PDF
```

---

Our Product
AI QA Automation Architect Platform

Input:

Jira Ticket

Output:

✔ Requirement Analysis

✔ Test Strategy

✔ Test Plan

✔ Test Cases

✔ Store into RAG

✔ Ask Questions

✔ Email Report

✔ Dashboard

---

## Sprint Plan
Sprint 1 — Foundation
Repository structure
FastAPI backend
Langflow setup
n8n setup
OpenRouter
ChromaDB
Health checks
Sprint 2 — Requirement Intelligence Agent

Input:

{
  "ticketId": "QA-101"
}

Output:

{
  "summary": "...",
  "businessRules": [],
  "risks": [],
  "assumptions": [],
  "missingRequirements": [],
  "testScope": []
}
Sprint 3 — Test Plan Agent

Uses:

skill.md
requirement output

Produces:

Markdown
HTML
JSON
Sprint 4 — Test Design Agent

Produces:

Functional
Positive
Negative
Boundary
Edge
Regression
Sprint 5 — RAG

Stores every generated artifact:

Requirement
Test Plan
Test Cases

Then enables:

"Show all negative test cases for Login."

or

"Why was TC-104 created?"

Sprint 6 — Reporting Agent

Generates:

Markdown
HTML
PDF
Email summary
Sprint 7 — Dashboard

Shows:

Tickets
Generated plans
Test cases
AI execution logs

-----------------------------------------------------
Agent Design

We're building a team of AI agents, not one giant prompt.

Agent 1

Requirement Intelligence

Input:

Jira Ticket

Output:

Structured Requirement JSON
Agent 2

Test Strategy

Input:

Requirement JSON

Output:

Strategy JSON
Agent 3

Test Plan

Uses your skill.md.

Output:

Markdown
HTML
JSON
Agent 4

Test Designer

Produces all test cases.

Agent 5

Knowledge Manager

Stores everything in ChromaDB.

Agent 6

RAG Explorer

Answers questions.

Agent 7

Reporting Agent

Creates:

Email
HTML
PDF
Dashboard