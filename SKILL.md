---
name: ai-architecture-review
description: consulting-ready ai architecture review workflow for evaluating ai, llm, ml, agentic ai, rag, automation, and decision-support system designs. use when the user asks for an architecture review, risk analysis, system diagram, go/no-go assessment, technical due diligence, ai solution audit, implementation critique, or customer-facing recommendations for an ai system. produces executive-ready findings, mermaid system diagrams, prioritized risk matrices, assumptions, open questions, and pragmatic next actions.
---

# AI Architecture Review

## Overview

Use this skill to produce consulting-ready reviews of AI system architectures. Focus on clear business decisions, defensible technical reasoning, practical risk treatment, and client-friendly recommendations.

Default to a polished advisory tone: direct, structured, concise, and actionable. Avoid academic sprawl. Make uncertainty explicit.

## Default workflow

1. Clarify the review scope only when required to avoid a misleading review. If enough context exists, proceed with stated assumptions.
2. Extract the architecture from the provided text, files, links, diagrams, code snippets, or meeting notes.
3. Identify system actors, data flows, model flows, tool calls, storage, governance checkpoints, and operational dependencies.
4. Create or refine a system diagram using Mermaid unless the user asks for another format.
5. Evaluate risks using the rubric in `references/risk-rubric.md`.
6. Structure the final response using `references/report-template.md`.
7. Use `references/diagram-guidelines.md` for diagram conventions and Mermaid patterns.
8. End with prioritized recommendations and a decision stance: go, conditional go, no-go, or needs discovery.

## Input handling

Accept any of these inputs:

- Architecture descriptions, implementation plans, PRDs, proposals, workshop notes, or strategy docs.
- Uploaded PDFs, docs, slides, screenshots, diagrams, spreadsheets, or exported notes.
- Code snippets, repository summaries, API descriptions, data schemas, logs, prompts, or agent tool definitions.
- Links or connector-based sources when available.

If the user provides connected-source links or asks for company/project context, use available connectors or file search before reviewing. Cite retrieved sources when the environment supports citations. If sources are incomplete, state what was and was not reviewed.

## Review stance

Be consulting-ready:

- Lead with what matters for decision-makers.
- Separate facts, assumptions, inferences, and recommendations.
- Prefer practical mitigation plans over abstract warnings.
- Flag severe architectural flaws plainly.
- Avoid false certainty. Use confidence levels when evidence is thin.
- Translate technical risk into business impact.
- Keep the output useful for client meetings, steering committees, and implementation planning.

## Required output qualities

Every substantial review should include:

- Executive summary with decision stance.
- Architecture understanding in plain language.
- Mermaid system diagram when enough structure is available.
- Risk matrix with severity, likelihood, priority, evidence, and mitigation.
- Top recommendations ordered by impact and urgency.
- Open questions and validation steps.
- Assumptions and review limitations.

## Diagram expectations

Create diagrams that help the user reason, not decorative diagrams. Prefer one clear high-level system diagram over several noisy diagrams. Use Mermaid `flowchart LR` by default.

Read `references/diagram-guidelines.md` before producing complex diagrams.

## Risk assessment expectations

Use the rubric in `references/risk-rubric.md`. Adapt categories to the architecture, but always consider:

- Security and access control.
- Privacy, data protection, and data retention.
- Prompt injection, tool abuse, and agent autonomy risks.
- Model quality, hallucination, evaluation, and monitoring.
- RAG/data grounding quality where relevant.
- Human-in-the-loop controls and escalation paths.
- Reliability, availability, rollback, and incident response.
- Cost, latency, scaling, and vendor lock-in.
- Compliance, auditability, and accountability.
- UX failure modes and user trust.

## Final report structure

Use `references/report-template.md` as the default format. Adapt only when the user requests a different deliverable, such as a short memo, slide outline, due diligence checklist, or implementation backlog.

## Recommendation style

For each recommendation, specify:

- What to change.
- Why it matters.
- Owner or accountable function when inferable.
- Effort level: low, medium, or high.
- Expected impact: low, medium, or high.
- Timing: now, next sprint, before launch, or post-launch.

## Decision stance rules

Use these default definitions:

- **go**: material risks are understood, controlled, and compatible with the intended use.
- **conditional go**: viable if named mitigations are completed before launch or scale-up.
- **no-go**: unacceptable unresolved risk, missing critical controls, or architecture is not fit for purpose.
- **needs discovery**: not enough evidence to judge responsibly.

## Common user requests

For "review this architecture", provide the full report.

For "make a system diagram", focus on Mermaid and explain notable flows or missing components.

For "risk analysis only", skip broad architecture commentary and produce the risk matrix plus mitigations.

For "make it client-ready", polish language, prioritize executive clarity, and include decision-ready next steps.

For "turn this into actions", produce an implementation backlog grouped by risk area and urgency.
