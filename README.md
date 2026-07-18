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


------------------------------------
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
-----------------------------------------------


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


                        Sprint Plan
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