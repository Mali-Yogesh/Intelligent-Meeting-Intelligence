# 🧠 AI Meeting Intelligence System

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/yourusername/ai-project)
[![Python](https://img.shields.io/badge/python-3.11-green.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.104.1-teal.svg)](https://fastapi.tiangolo.com/)
[![Docker](https://img.shields.io/badge/Docker-Ready-blue.svg)](https://www.docker.com/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

## 📋 Overview

**AI Meeting Intelligence System** ek powerful tool hai jo unstructured meeting conversations, transcripts, aur summaries ko **structured, queryable business intelligence** mein convert karta hai. Yeh system AI ka use karke automatically extract karta hai:

- ✅ Projects & Initiatives
- ✅ Action Items & Task Ownership
- ✅ Blockers & Unresolved Issues
- ✅ Risks & Dependencies
- ✅ Stakeholders & Accountable Parties
- ✅ Timelines & Deadlines
- ✅ Priority Levels
- ✅ Key Decisions & Rationale
- ✅ Follow-up Actions

## 🎯 Problem Statement

Organizations mein daily hundreds of meetings hoti hain, lekin unmein discussed crucial information often **lost** ho jaati hai. Manual tracking is:
- ❌ Time-consuming
- ❌ Error-prone
- ❌ Inconsistent
- ❌ Non-scalable

**Our solution** automatically extracts aur structures yeh information, making it **searchable, queryable, and actionable**.

## ✨ Features

### Core Capabilities

| Feature | Description |
|---------|-------------|
| **Multi-format Input** | Accepts text, raw transcripts, PDF files |
| **AI-Powered Extraction** | Uses GPT-4 (with fallback mock mode) to extract structured data |
| **Graph Database Storage** | Neo4j for relationship mapping (people↔tasks↔projects) |
| **Vector Search** | ChromaDB for semantic similarity search |
| **Natural Language Query** | Ask questions in plain English |
| **Real-time Insights** | Dashboard for escalations, project health, accountability gaps |
| **Slack Alerts** | Automatic notifications for high-risk items |

### Bonus Features
- 🔄 Multi-agent extraction workflow
- 📊 Risk severity scoring engine
- 🔍 Duplicate escalation detection
- 📧 Auto-generated follow-up emails
- 💬 Slack/Teams integration

## 🏗️ Architecture

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                                    PRESENTATION LAYER                                 │
│  ┌──────────────────────────────────────────────────────────────────────────────┐   │
│  │                         Frontend (Port 80)                                    │   │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐        │   │
│  │  │   HTML5     │  │    CSS3     │  │ JavaScript  │  │  Nginx      │        │   │
│  │  │  Structure  │  │  Styling    │  │   Logic     │  │  Server     │        │   │
│  │  └─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘        │   │
│  └──────────────────────────────────────────────────────────────────────────────┘   │
│                                          │                                          │
│                                    HTTP/HTTPS                                       │
│                                          ▼                                          │
└─────────────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                                     API GATEWAY LAYER                                │
│  ┌──────────────────────────────────────────────────────────────────────────────┐   │
│  │                         FastAPI Backend (Port 8000)                           │   │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐    │   │
│  │  │   Ingestion  │  │   Query      │  │  Insights    │  │   Health     │    │   │
│  │  │  Endpoints   │  │  Endpoints   │  │  Endpoints   │  │  Endpoints   │    │   │
│  │  └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘    │   │
│  │                                                                              │   │
│  │  ┌────────────────────────────────────────────────────────────────────┐    │   │
│  │  │                    Middleware Layer                                 │    │   │
│  │  │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ │    │   │
│  │  │  │   CORS   │ │  Rate    │ │   Auth   │ │  Logging │ │  Cache   │ │    │   │
│  │  │  │          │ │ Limiting │ │          │ │          │ │  (Redis) │ │    │   │
│  │  │  └──────────┘ └──────────┘ └──────────┘ └──────────┘ └──────────┘ │    │   │
│  │  └────────────────────────────────────────────────────────────────────┘    │   │
│  └──────────────────────────────────────────────────────────────────────────────┘   │
│                                          │                                          │
└──────────────────────────────────────────┼──────────────────────────────────────────┘
                                           │
                            ┌──────────────┼──────────────┐
                            │              │              │
                            ▼              ▼              ▼
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                                  AI PROCESSING LAYER                                 │
│  ┌──────────────────────────────────────────────────────────────────────────────┐   │
│  │                         Extraction Engine                                     │   │
│  │  ┌────────────────────────────────────────────────────────────────────┐      │   │
│  │  │                     Orchestrator                                    │      │   │
│  │  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐             │      │   │
│  │  │  │  Preprocess  │→│   LLM Call   │→│  Postprocess │             │      │   │
│  │  │  │   (Clean)    │  │   (GPT-4)    │  │  (Validate)  │             │      │   │
│  │  │  └──────────────┘  └──────────────┘  └──────────────┘             │      │   │
│  │  └────────────────────────────────────────────────────────────────────┘      │   │
│  │                                                                              │   │
│  │  ┌────────────────────────────────────────────────────────────────────┐      │   │
│  │  │                    Fallback Extractor (Mock Mode)                   │      │   │
│  │  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐             │      │   │
│  │  │  │    Regex     │  │   Keyword    │  │  Temporal    │             │      │   │
│  │  │  │   Matcher    │  │   Detector   │  │   Parser     │             │      │   │
│  │  │  └──────────────┘  └──────────────┘  └──────────────┘             │      │   │
│  │  └────────────────────────────────────────────────────────────────────┘      │   │
│  │                                                                              │   │
│  │  ┌────────────────────────────────────────────────────────────────────┐      │   │
│  │  │                    Entity Recognition Pipeline                      │      │   │
│  │  │  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐│      │   │
│  │  │  │ Person │ │Project │ │  Task  │ │ Date   │ │ Risk   │ │Blocker ││      │   │
│  │  │  │  NER   │ │  NER   │ │  NER   │ │  NER   │ │  NER   │ │  NER   ││      │   │
│  │  │  └────────┘ └────────┘ └────────┘ └────────┘ └────────┘ └────────┘│      │   │
│  │  └────────────────────────────────────────────────────────────────────┘      │   │
│  └──────────────────────────────────────────────────────────────────────────────┘   │
│                                          │                                          │
└──────────────────────────────────────────┼──────────────────────────────────────────┘
                                           │
                            ┌──────────────┼──────────────┐
                            │              │              │
                            ▼              ▼              ▼
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                                   STORAGE LAYER                                      │
│  ┌─────────────────────────────┐  ┌─────────────────────────────┐                  │
│  │       Neo4j (Graph DB)      │  │     ChromaDB (Vector DB)     │                  │
│  │         Port: 7687          │  │         Port: 8001           │                  │
│  │  ┌───────────────────────┐  │  │  ┌───────────────────────┐  │                  │
│  │  │       Nodes           │  │  │  │    Collections        │  │                  │
│  │  │  ┌─────────────────┐  │  │  │  │  ┌─────────────────┐  │  │                  │
│  │  │  │ • Meeting       │  │  │  │  │  │ meeting_entities│  │  │                  │
│  │  │  │ • Project       │  │  │  │  │  └─────────────────┘  │  │                  │
│  │  │  │ • Person        │  │  │  │  │                       │  │                  │
│  │  │  │ • Task          │  │  │  │  │  ┌─────────────────┐  │  │                  │
│  │  │  │ • Blocker       │  │  │  │  │  │   Embeddings    │  │  │                  │
│  │  │  │ • Risk          │  │  │  │  │  │  (384-dim)      │  │  │                  │
│  │  │  │ • Escalation    │  │  │  │  │  └─────────────────┘  │  │                  │
│  │  │  │ • Team          │  │  │  │  │                       │  │                  │
│  │  │  │ • FollowUp      │  │  │  │  │  ┌─────────────────┐  │  │                  │
│  │  │  └─────────────────┘  │  │  │  │  │   Metadata      │  │  │                  │
│  │  │       Relationships    │  │  │  │  │ • type          │  │  │                  │
│  │  │  ┌─────────────────┐  │  │  │  │  │ • meeting_id    │  │  │                  │
│  │  │  │ • DISCUSSED     │  │  │  │  │  │ • owner         │  │  │                  │
│  │  │  │ • ASSIGNED_TO   │  │  │  │  │  │ • timestamp     │  │  │                  │
│  │  │  │ • HAS_BLOCKER   │  │  │  │  │  └─────────────────┘  │  │                  │
│  │  │  │ • RAISED_IN     │  │  │  │  │                       │  │                  │
│  │  │  │ • DEPENDS_ON    │  │  │  │  │  ┌─────────────────┐  │  │                  │
│  │  │  │ • CREATED       │  │  │  │  │  │  Similarity     │  │  │                  │
│  │  │  │ • MUST_FOLLOW   │  │  │  │  │  │    Index        │  │  │                  │
│  │  │  └─────────────────┘  │  │  │  │  └─────────────────┘  │  │                  │
│  │  └───────────────────────┘  │  │  └───────────────────────┘  │                  │
│  └─────────────────────────────┘  └─────────────────────────────┘                  │
│                                                                                      │
│  ┌─────────────────────────────┐  ┌─────────────────────────────┐                  │
│  │      Redis (Cache)          │  │    File Storage (PDF/TXT)    │                  │
│  │         Port: 6379          │  │                              │                  │
│  │  ┌───────────────────────┐  │  │  ┌───────────────────────┐  │                  │
│  │  │ • Query Results Cache │  │  │  │ • Raw Meeting Files   │  │                  │
│  │  │ • Session Storage     │  │  │  │ • Processed Outputs   │  │                  │
│  │  │ • Rate Limit Counters │  │  │  │ • Historical Data     │  │                  │
│  │  └───────────────────────┘  │  │  └───────────────────────┘  │                  │
│  └─────────────────────────────┘  └─────────────────────────────┘                  │
└─────────────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                                 QUERY PROCESSING LAYER                               │
│  ┌──────────────────────────────────────────────────────────────────────────────┐   │
│  │                         Query Router                                          │   │
│  │  ┌────────────────────────────────────────────────────────────────────┐      │   │
│  │  │              Intent Classifier                                     │      │   │
│  │  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐              │      │   │
│  │  │  │   Graph      │  │  Semantic    │  │   Hybrid     │             │      │   │
│  │  │  │   Queries    │  │   Queries    │  │   Queries    │             │      │   │
│  │  │  └──────────────┘  └──────────────┘  └──────────────┘             │      │   │
│  │  └────────────────────────────────────────────────────────────────────┘      │   │
│  │                                                                              │   │
│  │  ┌─────────────────────────────┐  ┌─────────────────────────────┐          │   │
│  │  │    Graph Query Executor     │  │  Semantic Query Executor    │          │   │
│  │  │  ┌───────────────────────┐  │  │  ┌───────────────────────┐  │          │   │
│  │  │  │  NL → Cypher          │  │  │  │  Text → Embedding     │  │          │   │
│  │  │  │  Transformer          │  │  │  │  Converter            │  │          │   │
│  │  │  └───────────────────────┘  │  │  └───────────────────────┘  │          │   │
│  │  │  ┌───────────────────────┐  │  │  ┌───────────────────────┐  │          │   │
│  │  │  │  Cypher Executor      │  │  │  │  Vector Search        │  │          │   │
│  │  │  │  (Neo4j Driver)       │  │  │  │  (ChromaDB)           │  │          │   │
│  │  │  └───────────────────────┘  │  │  └───────────────────────┘  │          │   │
│  │  │  ┌───────────────────────┐  │  │  ┌───────────────────────┐  │          │   │
│  │  │  │  Result Formatter     │  │  │  │  LLM Response         │  │          │   │
│  │  │  │                       │  │  │  │  Generator            │  │          │   │
│  │  │  └───────────────────────┘  │  │  └───────────────────────┘  │          │   │
│  │  └─────────────────────────────┘  └─────────────────────────────┘          │   │
│  └──────────────────────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                              NOTIFICATION & INSIGHTS LAYER                           │
│  ┌──────────────────────────────────────────────────────────────────────────────┐   │
│  │                         Analytics Engine                                      │   │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐    │   │
│  │  │   Metrics    │  │   Trends     │  │   Reports    │  │   Dashboard  │    │   │
│  │  │  Collector   │  │  Analyzer    │  │  Generator   │  │   Renderer   │    │   │
│  │  └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘    │   │
│  │                                                                              │   │
│  │  ┌────────────────────────────────────────────────────────────────────┐      │   │
│  │  │                      Alert Manager                                 │      │   │
│  │  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐              │      │   │
│  │  │  │  Risk Score  │→│   Threshold  │→│   Slack      │                │      │   │
│  │  │  │  Calculator  │  │   Checker    │  │  Webhook     │             │       │   │
│  │  │  └──────────────┘  └──────────────┘  └──────────────┘             │      │   │
│  │  │                           │                                       │      │   │
│  │  │                           ▼                                       │      │   │
│  │  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐             │      │   │
│  │  │  │   Email      │  │   SMS        │  │   Teams      │             │      │   │
│  │  │  │  Service     │  │  Service     │  │  Webhook     │             │      │   │
│  │  │  └──────────────┘  └──────────────┘  └──────────────┘             │      │   │
│  │  └────────────────────────────────────────────────────────────────────┘      │   │
│  └──────────────────────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                                 EXTERNAL INTEGRATIONS                                │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐                │
│  │   OpenAI    │  │    Slack    │  │   Email     │  │   Zoom      │                │
│  │   GPT-4 API │  │   Webhook   │  │   SMTP      │  │   API       │                │
│  └─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘                │
└─────────────────────────────────────────────────────────────────────────────────────┘
