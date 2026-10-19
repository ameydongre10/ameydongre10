<h1 align="center">Amey Dongre</h1>

<p align="center">
  <a href="https://git.io/typing-svg">
    <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=20&pause=1000&color=7928CA&center=true&vCenter=true&width=600&lines=AI+%26+ML+Engineer+in+the+Making;Building+RAG+Systems+%26+Data+Pipelines;B.Tech+CSE+%E2%80%94+PSIT+Kanpur+(2024%E2%80%932028);IEEE+RAS+Chair+%26+Technical+Community+Builder" alt="Typing SVG" />
  </a>
</p>

<p align="center">
  <a href="https://linkedin.com/in/amey-dongre-58a597321">
    <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn" />
  </a>
  &nbsp;
  <a href="mailto:amey.dongre2005@gmail.com">
    <img src="https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white" alt="Email" />
  </a>
  &nbsp;
  <a href="https://www.researchgate.net/profile/Amey-Dongre-2">
    <img src="https://img.shields.io/badge/ResearchGate-00CCBB?style=flat-square&logo=researchgate&logoColor=white" alt="ResearchGate" />
  </a>
  &nbsp;
  <img src="https://komarev.com/ghpvc/?username=ameydongre10&label=Profile+Views&color=7928ca&style=flat-square" alt="Profile Views" />
</p>

---

## About Me

I am a Computer Science and Engineering student at **PSIT Kanpur, AKTU** (2024–2028), working at the intersection of AI, machine learning, and practical software engineering.

My projects focus on **information retrieval systems, grounded LLM applications, and data analytics pipelines** — problems where correctness, explainability, and engineering rigor matter as much as raw capability. I'm particularly interested in the failure modes of AI systems and designing architectures that handle them predictably.

Outside of building, I lead technical communities through **IEEE PSIT** as IEEE RAS Chapter Chair and contribute to organising research tracks and student workshops. I enjoy problems that require thinking carefully about system design before writing the first line of code.

---

## Featured Projects

### [Enterprise Multi-Vector Hybrid RAG & Context Engineering Engine](https://github.com/ameydongre10/Enterprise-Multi-Vector-Hybrid-RAG-Search-Engine)

An asynchronous enterprise information retrieval system designed to solve four specific failure modes that cause standard RAG implementations to break on real-world unstructured corporate data (financial filings, medical records, legal contracts, tabular data).

**Core engineering decisions:**
- **Contextualized Parent-Child Chunking** — prepends a document-level summary header to every 512-token chunk before vectorisation, preserving global context within each retrieved fragment.
- **Dual-Path Hybrid Retrieval** — executes Dense Vector Search (768-dim Gemini embeddings via pgvector) and Sparse BM25 lexical search concurrently through thread pools, then fuses results using Reciprocal Rank Fusion (RRF).
- **Cross-Encoder Reranking** — a secondary scoring pass prunes the fused candidate pool to Top-5 contextually aligned results.
- **Grounded Citation Synthesis** — all answers are synthesised with inline citation tags tied to source metadata (document name, page number, raw snippet), with a RAGAS evaluation suite measuring Faithfulness, Answer Relevance, Context Recall, and Context Precision.
- **Non-blocking Ingestion** — multi-megabyte document uploads are processed as async background tasks (returning a task ID immediately), preventing HTTP thread starvation.

**Stack:** Python 3.11 · FastAPI · React 18 · PostgreSQL 16 + pgvector · Google Gemini 2.5 Flash · BM25Okapi · Sentence Transformers · RAGAS

**Live:** [Frontend](https://enterprise-multi-vector-hybrid-rag.vercel.app) · [Backend API](https://enterprise-multi-vector-hybrid-rag-search-engine.onrender.com) · [Swagger Docs](https://enterprise-multi-vector-hybrid-rag-search-engine.onrender.com/docs)

---

### [Artist Intelligence & Recommendation System (AIRS)](https://github.com/ameydongre10/artist-intelligence-recommendation-system)

A talent matching system built around the observation that keyword-search and black-box embedding recommenders frequently hallucinate capability assessments — treating self-reported profile claims the same as demonstrated portfolio evidence.

AIRS enforces a four-state **Epistemic Separation Model**: `DEMONSTRATED_EVIDENCE` (verified media, 1.0× weight), `CLAIM` (self-reported, 0.4× weight), `ASSUMPTION` (contextual inference, 0×), and `UNKNOWN` (neutral, 0 penalty — absence of evidence ≠ incapacity).

**Scoring architecture:** A fully deterministic formula bounded in [0, 100] decomposed into Requirement Fit (≤50 pts), Evidence Strength Bonus (≤30 pts), Constraint Baseline (20 pts), and Conflict Deductions. Outputs a strict Top-2 recommendation with a comparative trade-off analysis and at most two high-impact clarifying questions.

**Stack:** Python 3.10 · FastAPI · Next.js 14 (static export) · Render (primary + failover instances)

**Live:** [Web Console](https://ameydongre10.github.io/artist-intelligence-recommendation-system/) · [Primary API](https://artist-intelligence-recommendation-system-hhdt.onrender.com)

---

### [PharmaVigil](https://github.com/ameydongre10/PharmaVigil)

A portfolio prototype for grounded AI-assisted **Periodic Adverse Drug Experience Report (PADER)** generation, targeting the failure modes that make naive LLM integration unsafe in pharmacovigilance contexts (numeric hallucination, causality invention, absent audit trails).

**Architecture pattern:** Deterministic analysis layer runs all arithmetic before any LLM call; structured `EvidenceItem` packets (never raw DataFrames) are passed as LLM context; a regex-based number extraction audit verifies every figure in the generated narrative against pre-computed evidence; all outputs default to `DRAFT_PENDING_REVIEW` until a medical officer explicitly signs off.

Supports multi-provider LLM backends (OpenAI, Gemini, Anthropic, Mock), with 120 automated tests covering analysis, API, evidence isolation, grounding validation, and hardening edge cases.

> *Note: This is a portfolio/interview prototype, not validated software for regulatory submissions or clinical use.*

**Stack:** Python 3.11 · FastAPI · SQLite · OpenAI / Gemini / Anthropic · Pytest (120 tests)

**Live:** [Dashboard](https://ameydongre10.github.io/PharmaVigil/) · [API](https://pader-regulatory-engine.onrender.com) · [Swagger](https://pader-regulatory-engine.onrender.com/docs)

---

### [SpendSense](https://github.com/ameydongre10/SpendSense)

A payments-network analytics and fraud risk intelligence system modelling the analytical workflow of a senior risk and portfolio analytics engineer at a card scheme.

Runs a dual-track analysis on 284,807 anonymised card transactions (0.173% fraud rate): a **Risk Track** (XGBoost fraud classifier with cost-sensitive training and AUPRC evaluation against severe class imbalance) and a **Consumer Services Track** (RFM customer segmentation, cohort lifecycle analysis, customer segment profitability modelling). Outputs an interactive editorial dashboard and quantified commercial recommendations.

**Stack:** Python 3.11 · PostgreSQL · SQLite · XGBoost · scikit-learn · FastAPI · Vercel

**Live:** [Dashboard](https://spend-sense-blue-six.vercel.app)

---

## Technical Skills

**Languages**

[![Languages](https://skillicons.dev/icons?i=py,ts,js,java,cpp)](https://skillicons.dev)

**AI / ML & Data**

![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-189AA8?style=flat-square&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)

**Generative AI & RAG**

![Gemini](https://img.shields.io/badge/Google_Gemini-4285F4?style=flat-square&logo=google&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white)
![pgvector](https://img.shields.io/badge/pgvector-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Hybrid RAG](https://img.shields.io/badge/Hybrid_RAG_(BM25+Dense)-7928CA?style=flat-square)
![RAGAS](https://img.shields.io/badge/RAGAS_Eval-FF6B6B?style=flat-square)

**Backend & APIs**

[![Backend](https://skillicons.dev/icons?i=fastapi,nodejs,express)](https://skillicons.dev)

**Frontend**

[![Frontend](https://skillicons.dev/icons?i=react,nextjs,vite)](https://skillicons.dev)

**Databases**

[![Databases](https://skillicons.dev/icons?i=postgres,mongodb,mysql,redis)](https://skillicons.dev)

**DevOps & Tools**

[![DevOps](https://skillicons.dev/icons?i=docker,git,githubactions,linux,postman)](https://skillicons.dev)

---

## Experience & Leadership

| Role | Organization | Notes |
|------|-------------|-------|
| **AI/ML Intern** | FlyRank AI | Developing and evaluating ML models |
| **Chapter Chair** | IEEE Robotics & Automation Society (RAS), PSIT | Leading workshops and research tracks |
| **Branch Treasurer** | IEEE PSIT Student Branch | Operations, budgeting, and strategy |
| **Ex-Chapter Chair** | IEEE SIGHT, PSIT | Humanitarian technology initiatives |
| **Campus Ambassador** | Cognizance (IIT Roorkee) & Techkriti (IIT Kanpur) | Student outreach for national tech fests |

---

## Achievements

- **Top 100 Finalist — Hack Hatch 2025 (E-Cell, IIIT Delhi):** Selected among top 100 teams from 2,500+ nationwide participants.
- **1st Place — ProTech Event (PSIT Kanpur):** Technical presentation and project execution; covered in local news.
- **Global Rank 1146 — IEEE Xtreme 19.0:** 24-hour competitive programming contest; ranked 1,146 out of 8,169 registered teams worldwide.
- **IEEE VLSI Symposium (IIT Kanpur):** Attended *"Confluence of VLSI Minds 2025"* — IEEE Symposium on Microelectronics & VLSI.

---

## Certifications

| Certificate | Issuer |
|-------------|--------|
| Data Analytics Job Simulation | Deloitte Australia |
| Data Science Job Simulation | British Airways |
| AI Fluency for Students | AI/ML Principles & Applications |
| E-SUMMIT 2025 | Entrepreneurship & Technological Innovation |

---

## GitHub Analytics

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=ameydongre10&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" alt="Amey's GitHub Stats" width="48%" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=ameydongre10&layout=compact&theme=tokyonight&hide_border=true" alt="Top Languages" width="48%" />
</p>

<p align="center">
  <img src="https://streak-stats.demolab.com?user=ameydongre10&theme=tokyonight&hide_border=true" alt="GitHub Streak" width="97%" />
</p>

### Contribution Graph

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/ameydongre10/ameydongre10/output/github-snake-dark.svg" />
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/ameydongre10/ameydongre10/output/github-snake.svg" />
    <img alt="GitHub Contribution Snake" src="https://raw.githubusercontent.com/ameydongre10/ameydongre10/output/github-snake.svg" />
  </picture>
</p>

---

## Current Interests

I am actively exploring:
- **Retrieval-Augmented Generation** — hybrid retrieval architectures, reranking strategies, and hallucination-resistant grounding patterns.
- **ML for structured/tabular data** — fraud detection, anomaly scoring, and cost-sensitive classification under severe class imbalance.
- **Responsible AI system design** — epistemic uncertainty modelling, deterministic safety layers, and human-in-the-loop workflows.

---

## Connect

I am open to collaborating on projects in AI/ML systems, information retrieval, data engineering, and applied research. If you are working on something interesting, feel free to reach out.

<p align="center">
  <a href="https://linkedin.com/in/amey-dongre-58a597321">
    <img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin" alt="LinkedIn" />
  </a>
  &nbsp;&nbsp;
  <a href="mailto:amey.dongre2005@gmail.com">
    <img src="https://img.shields.io/badge/Email-amey.dongre2005@gmail.com-EA4335?style=flat-square&logo=gmail" alt="Email" />
  </a>
  &nbsp;&nbsp;
  <a href="https://github.com/ameydongre10">
    <img src="https://img.shields.io/badge/GitHub-ameydongre10-181717?style=flat-square&logo=github" alt="GitHub" />
  </a>
</p>
