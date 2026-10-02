# Mermaid Diagram Guidelines for AI Architecture Reviews

Use diagrams to make the architecture review faster to understand and easier to discuss with stakeholders.

## Default style

Use Mermaid `flowchart LR` unless the user asks for sequence, deployment, or process views.

Prefer readable component names over implementation jargon. Keep diagrams at one meaningful abstraction level.

## Common component groups

Use these groups when helpful:

- User and channels: web app, mobile app, chat, admin UI, API client.
- Application layer: backend, orchestration service, workflow engine, agent controller.
- AI layer: prompt layer, model router, LLM, embedding model, classifier, reranker.
- Knowledge layer: document store, vector DB, search index, knowledge base, metadata store.
- Tool layer: CRM, ERP, email, calendar, ticketing, database, browser, internal APIs.
- Control layer: policy engine, guardrails, approval workflow, audit logging, monitoring.
- Data layer: source systems, sensitive data store, analytics, logs, telemetry.

## High-level system diagram pattern

```mermaid
flowchart LR
    user[User or operator] --> channel[Product interface]
    channel --> app[Application backend]
    app --> policy[Policy and guardrail layer]
    policy --> orchestrator[AI orchestration]
    orchestrator --> model[Model provider or hosted model]
    orchestrator --> retrieval[Retrieval service]
    retrieval --> kb[Knowledge base or vector store]
    orchestrator --> tools[Approved tools and APIs]
    app --> audit[Audit logs and monitoring]
    policy --> human[Human review or approval]
```

## Agentic workflow pattern

Use this when an AI system can call tools or take actions.

```mermaid
flowchart LR
    user[User] --> agent[Agent controller]
    agent --> policy[Policy checks]
    policy --> planner[Planner]
    planner --> tool_router[Tool router]
    tool_router --> readonly[Read-only tools]
    tool_router --> write_tools[Write/action tools]
    write_tools --> approval[Human approval for high-impact actions]
    approval --> execution[Execution]
    execution --> audit[Audit trail]
    audit --> monitor[Monitoring and alerts]
```

## RAG pattern

Use this when the system uses retrieval-augmented generation.

```mermaid
flowchart LR
    sources[Source documents] --> ingestion[Ingestion and parsing]
    ingestion --> chunking[Chunking and metadata]
    chunking --> embeddings[Embedding model]
    embeddings --> vector[Vector store]
    user[User query] --> app[Application]
    app --> retriever[Retriever]
    retriever --> vector
    retriever --> context[Ranked context]
    context --> llm[LLM]
    llm --> answer[Answer with citations]
    app --> logs[Quality, cost, and audit logs]
```

## Diagram review checklist

Before finalizing a diagram, check:

- Are sensitive data flows visible?
- Are external vendors and APIs visible?
- Are human approval points visible?
- Are logs, monitoring, and audit trails visible?
- Are permission boundaries and tool boundaries visible?
- Is the diagram understandable without a long explanation?
