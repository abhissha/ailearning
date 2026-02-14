Pathway for AI Architect / AI Solutions Architect (Azure + .NET)

**Assumptions:** You already build/own Azure architectures, C#/.NET services, identity, observability, and enterprise governance. This plan adds *AI system design*, *LLM app patterns*, *agentic orchestration*, and *MLOps + Responsible AI*—with a heavy build focus.

---

## Outcomes you should be able to demonstrate (portfolio-ready)

By the end of 6 months you should have:
1. **A production-style RAG solution** on Azure (Azure OpenAI + Azure AI Search) with evaluation, observability, and cost controls.
2. **An agentic workflow** (tool-using agent) built in **.NET (Semantic Kernel)**, with **MCP** to standardize tool/data access.
3. **A reference architecture + ADR set** for GenAI in Azure: security, privacy, and governance baked in.
4. **A repeatable delivery playbook**: “how we build AI features safely” (guardrails, evals, incident response, SLAs/SLOs).

---

## Tooling setup (do this once, Day 0)
- Azure subscription with ability to deploy:
  - Azure OpenAI
  - Azure AI Search
  - App Service / Container Apps
  - Key Vault
  - App Insights / Log Analytics
- Dev stack:
  - .NET 8 SDK
  - VS / Rider
  - Docker
  - Python 3.11+ (optional but useful for eval scripts)
- Repo skeleton: `src/`, `infra/` (Bicep/Terraform), `docs/` (ADRs), `evals/`, `threat-model/`.

---

## AI architecture patterns you’ll apply repeatedly
Use these as “building blocks” across your projects:
- **RAG** (classic + hybrid search + re-ranking + citations)
- **Prompt + policy + tool orchestration** (function calling / plugins)
- **Agentic workflow** (planner–executor, supervisor–worker, reflection, human-in-the-loop)
- **Safety/Guardrails** (prompt injection defense, output filtering, policy gating)
- **Evaluation & Observability** (offline evals, online A/B, hallucination tests, latency/cost)
- **Caching** (prompt cache + embedding cache + retrieval cache)
- **Data governance** (PII redaction, access controls, audit trails)
- **MLOps/LLMOps** (versioning prompts, datasets, evals, deployment gates)

You’ll see these referenced throughout the schedule.

---

# Two-week acceleration (Daily schedule)

**Time per day:** ~1-2 hours (mix of learning + hands-on).  
**Goal:** get you to “build-first competence” fast: Azure OpenAI + RAG + .NET orchestration + safety + evaluation.

### Course/link index (used in order below)

**Pluralsight (PS)**
1. Getting Started with Azure OpenAI Service — https://www.pluralsight.com/courses/azure-openai-services-getting-started  
2. First Look: Azure OpenAI Services — https://www.pluralsight.com/courses/azure-openai-services-first-look  
3. Building AI-enabled .NET Applications — https://www.pluralsight.com/courses/building-ai-enabled-dot-net-applications  
4. Building AI Applications with Semantic Kernel and C# — https://www.pluralsight.com/courses/semantic-kernel-c-sharp-building-ai-applications  
5. Getting Started on Prompt Engineering with Generative AI — https://www.pluralsight.com/courses/getting-started-prompt-engineering-generative-ai  
6. Introduction to Azure AI Search — https://www.pluralsight.com/courses/introduction-to-azure-ai-search  
7. Retrieval Augmented Generation (RAG) with Azure AI Search — https://www.pluralsight.com/courses/retrieval-augmented-generation-rag-azure-ai-search  
8. Protecting Online Communities with Azure AI Content Safety — https://www.pluralsight.com/courses/protecting-online-communities-azure-ai-content-safety  
9. Introduction to MLOps on Azure — https://www.pluralsight.com/courses/introduction-to-mlops-on-azure  
10. Deploying Models with Azure Machine Learning — https://www.pluralsight.com/courses/deploying-models-azure-machine-learning  

**LinkedIn Learning (LI)**
1. GenAI and Predictive AI Architecture Foundations — https://www.linkedin.com/learning/genai-and-predictive-ai-architecture-foundations  
2. Introduction to Prompt Engineering for Generative AI — https://www.linkedin.com/learning/introduction-to-prompt-engineering-for-generative-ai-24636124  
3. Creating Generative AI Solutions and Copilots with Azure AI Foundry — https://www.linkedin.com/learning/creating-generative-ai-solutions-and-copilots-with-azure-ai-foundry-formerly-azure-ai-studio  
4. Azure OpenAI: Advanced Topics — https://www.linkedin.com/learning/azure-openai-advanced-topics  
5. AI Solution Design Patterns: Data, Model Training, and Application Architectures — https://www.linkedin.com/learning/ai-solution-design-patterns-data-model-training-and-application-architectures  
6. Building in Azure AI Foundry — https://www.linkedin.com/learning/building-in-azure-ai-foundry  

**Free / official**
- Azure Architecture Center: RAG solution design & evaluation guide — https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/rag/rag-solution-design-and-evaluation-guide  
- AI Architecture - https://learn.microsoft.com/en-us/azure/architecture/ai-ml/
- RAG in Azure AI Search overview — https://learn.microsoft.com/en-us/azure/search/retrieval-augmented-generation-overview  
- RAG quickstart (chat over your data) — https://learn.microsoft.com/en-us/azure/search/search-get-started-rag  
- Azure OpenAI RAG workshop sample — https://github.com/Azure-Samples/azure-openai-rag-workshop  
- Microsoft “Generative AI for Beginners” — https://learn.microsoft.com/en-us/shows/generative-ai-for-beginners/  
- Semantic Kernel docs — https://learn.microsoft.com/en-us/semantic-kernel/  
- Semantic Kernel Agent Framework — https://learn.microsoft.com/en-us/semantic-kernel/frameworks/agent/  
- OWASP Top 10 for LLM Apps — https://owasp.org/www-project-top-10-for-large-language-model-applications/  
- NIST AI RMF 1.0 (PDF) — https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf  
- NIST GenAI Profile (PDF) — https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf  

**MCP (Model Context Protocol)**
- MCP spec (canonical) — https://modelcontextprotocol.io/specification/2025-11-25  
- MCP docs/spec repo — https://github.com/modelcontextprotocol/modelcontextprotocol  

---

## Week 1

### Day 1 — Architectural framing + GenAI fundamentals
**Learn (2–3h)**
- LI #1: *GenAI and Predictive AI Architecture Foundations*  
- Free: Microsoft *Generative AI for Beginners* (skim lessons 1–3)

**Build (1–2h)**
- Create a repo: `ai-architect-portfolio`
- Add `/docs/adr/0001-scope.md`: “AI Architect track: why, what, success metrics”
- Draft a **reference architecture** diagram (even rough): client → API → orchestration → model → retrieval → telemetry

**Pattern focus:** system boundaries, model vs. app responsibilities, “where truth comes from” (RAG vs. parametric memory).

---

### Day 2 — Azure OpenAI core mechanics
**Learn (1–2h)**
- PS #1: *Getting Started with Azure OpenAI Service*  
- PS #2: *First Look: Azure OpenAI Services*

**Build (2–3h)**
- Deploy an Azure OpenAI resource (or use a sandbox).  
- Write a minimal `.NET` console app that calls chat completion and logs:
  - latency
  - token usage
  - prompt/response versions (store prompt template in repo)

**Pattern focus:** prompt templates, system prompts, temperature/top_p tradeoffs.

---

### Day 3 — Prompt engineering as an architectural tool
**Learn (1–2h)**
- PS #5: *Getting Started on Prompt Engineering with Generative AI*  
- LI #2: *Introduction to Prompt Engineering for Generative AI*

**Build (2–3h)**
- Create a small prompt library:
  - `prompts/system/*.md`
  - `prompts/tasks/*.md`
- Add unit tests for “prompt contract” (structure, required variables)
- Start a simple “golden set” (`/evals/golden.jsonl`) of 25 Q&A pairs relevant to your domain.

**Pattern focus:** prompt contracts, few-shot examples, structured outputs (JSON schema).

---

### Day 4 — .NET orchestration: Semantic Kernel essentials
**Learn (2–3h)**
- PS #3: *Building AI-enabled .NET Applications*  
- PS #4: *Building AI Applications with Semantic Kernel and C#*

**Build (1–2h)**
- Build a minimal SK kernel:
  - a plugin/tool that calls a local function (e.g., “getTime”, “getPolicySnippet”)
  - add structured tool outputs
- Log tool invocations and reasoning traces (what was called, with what inputs)

**Pattern focus:** tool use, plugins/functions, separation of “reasoning” from “actions”.

---

### Day 5 — Azure AI Search foundations (for RAG)
**Learn (1–2h)**
- PS #6: *Introduction to Azure AI Search*  

**Build (2–3h)**
- Provision Azure AI Search.
- Index a small doc set (your own docs / public docs) and test:
  - keyword search
  - vector search (if enabled) or prepare for it
- Add retrieval results to logs (top K, scores, doc ids)

**Pattern focus:** chunking strategy, metadata, permissions, and “retrieval quality as a first-class metric”.

---

### Day 6 — RAG pattern (classic) end-to-end
**Learn (1–2h)**
- PS #7: *RAG with Azure AI Search*  
- Free: Microsoft RAG quickstart

**Build (2–3h)**
- Implement **classic RAG** in .NET:
  1) query → search → top K passages  
  2) compose grounded prompt with citations  
  3) model generates answer with cited sources  
- Add basic evaluation: answer must include citations; fail test if none.

**Pattern focus:** grounding + citations, retrieval-first thinking.

---

### Day 7 — RAG design & evaluation (architect-grade)
**Learn (2–3h)**
- Azure Architecture Center RAG design/eval guide (read carefully)
- RAG in Azure AI Search overview (skim)

**Build (1–2h)**
- Add `/docs/rag/`:
  - chunking ADR
  - retrieval ADR (BM25 vs hybrid vs vector)
  - evaluation plan (offline + online)
- Define 5 measurable KPIs: groundedness, relevance, latency p95, cost/query, refusal rate.

**Pattern focus:** evaluation loops, measurement-driven architecture.

---

## Week 2

### Day 8 — Safety, security, and risk controls (LLM apps)
**Learn (2–3h)**
- PS #8: *Azure AI Content Safety*  
- OWASP Top 10 for LLM Apps (read + map to mitigations)

**Build (1–2h)**
- Add safety middleware:
  - input filtering / prompt injection checks
  - output moderation
  - “policy gate” for sensitive topics
- Create a **threat model** (`/threat-model/llm-threats.md`) with mitigations.

**Pattern focus:** prompt injection, sensitive data leakage, excessive agency.

---

### Day 9 — Azure AI Foundry (formerly AI Studio): productized delivery flow
**Learn (2–3h)**
- LI #3: *Creating Generative AI Solutions and Copilots with Azure AI Foundry*
- LI #6: *Building in Azure AI Foundry* (start it; finish on Day 10)

**Build (1–2h)**
- Reproduce your RAG pipeline in Foundry (or map the equivalent).
- Document “Dev → Eval → Deploy” for your org.

**Pattern focus:** platformization, governance-friendly deployment pathways.

---

### Day 10 — Advanced Azure OpenAI practices
**Learn (1–2h)**
- LI #4: *Azure OpenAI: Advanced Topics*  
- Finish remaining sections of LI #6 as needed

**Build (2–3h)**
- Add:
  - prompt versioning
  - model selection config (router rules or static)
  - retry/backoff + circuit breaker
  - caching (prompt + retrieval)
- Add cost reporting: tokens/query into logs.

**Pattern focus:** reliability, cost controls, “AI is a dependency”.

---

### Day 11 — AI solution design patterns (beyond GenAI)
**Learn (2–3h)**
- LI #5: *AI Solution Design Patterns: Data, Model Training, and Application Architectures*

**Build (1–2h)**
- Write a one-page “AI architecture decision guide”:
  - when to use GenAI vs classic ML vs rules
  - when to fine-tune vs RAG
  - build/buy decision framework

**Pattern focus:** selecting the right AI approach.

---

### Day 12 — MLOps/LLMOps foundations (release engineering for AI)
**Learn (1–2h)**
- PS #9: *Introduction to MLOps on Azure*  
- PS #10: *Deploying Models with Azure Machine Learning* (short course)

**Build (2–3h)**
- Add CI checks:
  - prompt linting
  - retrieval regression tests (top K stability)
  - eval run gating (golden set)
- Add a release checklist for AI features.

**Pattern focus:** “tests as guardrails”, reproducibility, drift readiness.

---

### Day 13 — MCP (Model Context Protocol) + tool standardization
**Learn (1–2h)**
- Read MCP spec overview + repo docs:
  - https://modelcontextprotocol.io/specification/2025-11-25
  - https://github.com/modelcontextprotocol/modelcontextprotocol

**Build (2–3h)**
- Design an **MCP server** for your portfolio that exposes:
  - `search_docs(query)`
  - `get_policy(topic)`
  - `create_ticket(title, body)` (mock)
- Create an “agent tool policy”:
  - allowed tools
  - required logging/audit
  - data classification constraints

**Pattern focus:** standard tool/data access, least privilege, enterprise governance.

---

### Day 14 — Capstone for the acceleration: “RAG + Agent + Safety”
**Build (3–5h)**
- Deliver a working demo:
  - Chat endpoint (ASP.NET minimal API)
  - RAG grounding with citations
  - Safety layer (input/output)
  - Agent can call MCP tools for actions
- Record a short demo video script in `/docs/demo-script.md`.

**Pattern focus:** end-to-end, demoable outcomes.

---

# Weeks 3–6 (Build-focused sprint)

**Time budget:** You still have “a lot of free time” in week 3; after that, shift toward ~6 hrs/week.  
**Goal:** turn the Week 1–2 prototype into an “architect-grade” solution with real engineering maturity.

## Week 3 — Hardening + infrastructure-as-code
Deliverables:
- Bicep/Terraform to deploy: OpenAI, AI Search, App Insights, Key Vault
- Managed identity end-to-end
- Config/secret hygiene (no keys in appsettings)
Build tasks:
- Add streaming responses + cancellation
- Add per-request trace IDs; correlate retrieval + model call + tool calls

## Week 4 — Evaluation and observability (make it measurable)
Deliverables:
- Offline eval harness (`/evals/`)
- Dashboards: latency, cost, groundedness proxy, refusal rate
Build tasks:
- Add “answer quality rubric” (simple scoring)
- Add regression suite for retrieval + prompt
- Define SLOs for: p95 latency and max cost/query

## Week 5 — Agentic workflows (single + multi-agent patterns)
Deliverables:
- A planner–executor agent that:
  - plans steps
  - uses MCP tools
  - asks for human confirmation before “write” operations
Build tasks:
- Implement “excessive agency” guardrails:
  - tool call limits
  - confirmation prompts
  - role-based tool availability

## Week 6 — Security and governance packaging
Deliverables:
- Threat model + mitigations mapped to OWASP LLM Top 10
- An “AI governance checklist” doc:
  - data classification
  - logging/audit
  - red-teaming scenarios
Build tasks:
- Add a jailbreak/prompt-injection test set
- Add safe-fail behavior:
  - degrade to retrieval-only answers
  - refuse + escalate

---

# Six-month plan (includes the 2-week acceleration + weeks 3–6 build sprint)

## Month 1 (Weeks 1–4): Build competence + platform familiarity
- Weeks 1–2: **Two-week acceleration** (above)
- Weeks 3–4: Hardening + observability + evals (Weeks 3–4 above)

**Checkpoint:** You can explain + defend a full Azure GenAI architecture with measurements.

## Month 2 (Weeks 5–8): Agentic AI + MCP + enterprise patterns (6 hrs/week)
Focus:
- Implement richer agent patterns (supervisor/worker, reflection)
- Expand MCP server toolset and policy gating
- Add “enterprise integration” examples:
  - ticket creation (mock Jira/ServiceNow)
  - knowledge base search
  - approvals workflow

Deliverables:
- “Agent safety” playbook (tool limits, confirmations, audit)

## Month 3 (Weeks 9–12): Data & retrieval depth (6 hrs/week)
Focus:
- Better chunking (semantic + layout-aware)
- Hybrid retrieval + reranking
- Document ingestion pipeline (incremental updates, dedup, metadata)
- Multi-tenant permission trimming (architect-level story)

Deliverables:
- Retrieval evaluation report (before/after)
- Clear cost model and scaling plan

## Month 4 (Weeks 13–16): Responsible AI + security + compliance posture (6 hrs/week)
Focus:
- NIST AI RMF + GenAI Profile mapping to your architecture
- OWASP LLM Top 10 threat modeling & testing
- Privacy/PII patterns:
  - redaction
  - encryption boundaries
  - audit & retention

Deliverables:
- A “Responsible AI” appendix for your reference architecture
- Security test suite for LLM-specific threats

## Month 5 (Weeks 17–20): MLOps/LLMOps maturity + production readiness (6 hrs/week)
Focus:
- CI/CD with eval gates
- Canary rollout strategy for prompts/models
- Incident response for AI features (hallucination incidents, data leaks)
- Observability maturity (semantic logs, tool traces)

Deliverables:
- Release checklist + runbook
- Automated quality gate in pipeline

## Month 6 (Weeks 21–24): Packaging for interviews + real-world case studies (6 hrs/week)
Focus:
- Create 2–3 “architecture stories”:
  1) RAG-based copilot with governance
  2) Agentic workflow with MCP tools
  3) Security-first GenAI rollout
- Write an “AI Architecture Decision Guide” (polished)
- Optional: align study with **AI-102** (Azure AI Engineer) topics

Deliverables:
- Portfolio README with diagrams, ADRs, demo steps
- 10-slide “AI Architecture deck” (export from markdown if desired)

---

# Agentic AI: what it is and where it’s useful

## What “agentic” means in practice
An **agent** is an LLM-driven component that can:
- plan steps,
- call tools,
- observe results,
- and iterate toward a goal—often with constraints and human approvals.

## High-value enterprise use cases (good for an AI Architect portfolio)
- **IT / Ops copilots**: summarize incidents, propose remediation steps, open tickets with confirmation.
- **Knowledge + compliance assistants**: answer policy questions with citations + risk flags.
- **Developer productivity**: code review helpers, architecture ADR drafting, migration planning.
- **Customer support**: grounded answers with CRM/tool access (strict safety + escalation).
- **Finance/Procurement**: compare vendors, draft RFP responses with traceable sources.

## Key agentic patterns to learn and demonstrate
- **Planner–Executor:** one component plans, another executes tool calls.
- **Supervisor–Worker (multi-agent):** supervisor delegates tasks, workers specialize.
- **Reflection/critique:** second pass to check correctness, groundedness, and policy.
- **Human-in-the-loop:** agent requests approval before irreversible actions.
- **Tool governance:** least-privilege tool access + auditing.

## Failure modes you must design against
- Prompt injection leading to tool misuse
- Excessive agency (taking actions user didn’t intend)
- Hallucinated tool outputs / fabricated citations
- Data leakage across tenants or classifications

---

# MCP: how to incorporate it (architecturally)
MCP gives you a **standard way to expose tools and data** to LLM apps/agents.

## How MCP fits into your Azure architecture
- **LLM app / agent orchestrator** (your .NET service) connects to:
  - **MCP servers** that provide tool APIs + schemas + secure access patterns.
- Benefits:
  - decouples tool providers from agent code
  - makes tool catalogs governable (RBAC, audit, approvals)
  - supports consistent logging and policy enforcement

## Suggested MCP portfolio “tool catalog”
- Read tools:
  - `search_docs`
  - `get_policy_snippet`
  - `get_incident_status`
- Write tools (require confirmation):
  - `create_ticket`
  - `notify_channel`
  - `update_kb_article`

## MCP guardrails (must-have)
- Tool allowlist per role
- Explicit confirmation for write actions
- Rate limits + tool call budgets
- Full audit log of tool inputs/outputs

---

# Weekly rhythm after week 3 (6 hours/week)
Use a simple cadence:
- **2h** learning (one course/module chunk)
- **3h** build (feature + tests)
- **1h** architecture (ADRs + diagram + risk review)

---

## Suggested next-step learning (optional expansion)
If you want more depth later:
- Pluralsight: *Azure AI Services* path — https://www.pluralsight.com/paths/azure-ai-services  
- Pluralsight: *RAG for Developers* path — https://www.pluralsight.com/paths/retrieval-augmented-generation-rag-for-developers  
- LinkedIn: *Building Generative AI Skills for Developers* path — https://www.linkedin.com/learning/paths/building-generative-ai-skills-for-developers  

---

## Appendix: “Architect interview” artifacts to produce
- 1 reference architecture diagram + deployment view + data flow
- 6–10 ADRs (chunking, retrieval, model choice, eval, safety, MCP integration)
- Threat model mapped to OWASP LLM Top 10
- Evaluation report with metrics and trade-offs
- Demo walkthrough + runbook

