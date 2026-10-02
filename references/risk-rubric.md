# AI Architecture Risk Rubric

Use this rubric to evaluate AI, LLM, RAG, agentic AI, ML, automation, and decision-support architectures.

## Scoring model

Rate each risk on three dimensions:

- Severity: low, medium, high, critical.
- Likelihood: low, medium, high.
- Priority: p0, p1, p2, p3.

Priority guidance:

- p0: must address immediately. Launch or scale-up should stop until resolved.
- p1: address before launch, before customer exposure, or before wider rollout.
- p2: plan and schedule; acceptable only with monitoring or compensating controls.
- p3: track as improvement or operational hardening.

## Core risk categories

### 1. Strategic fit and value risk

Check whether the AI system solves a real business problem and whether AI is necessary.

Look for:

- Weak problem definition.
- Missing success metrics.
- Over-automation where workflow redesign would be simpler.
- Unclear human ownership.
- Benefits that depend on unrealistic model accuracy.

### 2. Data and privacy risk

Check how data is collected, processed, stored, retained, and exposed.

Look for:

- Sensitive data in prompts, logs, embeddings, traces, analytics, or vendor systems.
- Missing data classification.
- Unclear retention and deletion policies.
- Cross-border data transfer concerns.
- Unclear consent, legal basis, or purpose limitation.
- Training or fine-tuning on data without governance.

### 3. Security risk

Check whether the system can be abused or accessed by unauthorized parties.

Look for:

- Weak authentication or authorization.
- Over-broad service accounts or API keys.
- Missing secret handling.
- Insecure plugin, tool, or function-calling boundaries.
- Prompt injection leading to data exfiltration or unsafe actions.
- Lack of input/output filtering where needed.

### 4. Agentic and tool-use risk

For systems that can call tools, write data, trigger workflows, or take actions.

Look for:

- Tools with excessive permissions.
- No allowlist or policy layer.
- Missing human approval for irreversible or high-impact actions.
- Unclear rollback.
- Autonomy level not aligned with risk level.
- Tool outputs trusted without validation.

### 5. Model quality and reliability risk

Check whether model behavior is evaluated, monitored, and bounded.

Look for:

- No evaluation set.
- No golden tasks or acceptance thresholds.
- No regression testing after prompt/model changes.
- Hallucination risk in high-stakes contexts.
- Missing confidence handling or fallback behavior.
- No monitoring of drift, refusals, latency, or quality.

### 6. RAG and knowledge grounding risk

For retrieval-augmented generation or knowledge systems.

Look for:

- Poor document chunking or metadata strategy.
- Stale, duplicate, or conflicting knowledge sources.
- Missing source attribution.
- No retrieval evaluation.
- Permission leakage in retrieval.
- Embedding store not aligned with access control.

### 7. Human-in-the-loop and accountability risk

Check whether humans remain appropriately responsible.

Look for:

- Unclear review responsibility.
- Missing escalation paths.
- No audit trail for AI-assisted decisions.
- Users cannot contest, correct, or override outputs.
- AI output presented as definitive when it should be advisory.

### 8. Operational and MLOps/LLMOps risk

Check production readiness.

Look for:

- No deployment pipeline.
- No observability for prompts, retrieval, model calls, cost, and errors.
- No incident response plan.
- No versioning of prompts, tools, datasets, and models.
- No rollback strategy.
- Weak testing across environments.

### 9. Cost, latency, and scale risk

Check whether the system can operate sustainably.

Look for:

- Token-heavy workflows without budget controls.
- Expensive model used for low-value tasks.
- Latency unacceptable for user journey.
- No caching, batching, routing, or model tiering strategy.
- Vendor pricing changes could break economics.

### 10. Compliance and governance risk

Check whether the system is auditable and aligned with applicable policy.

Look for:

- Missing risk classification.
- No documented controls.
- No audit evidence.
- Missing owner for model/system governance.
- Unclear use restrictions.
- No review cadence.

## Risk matrix row format

Use this format:

| ID | Risk | Category | Severity | Likelihood | Priority | Evidence | Business impact | Recommendation |
|---|---|---|---|---|---|---|---|---|
| R1 | ... | ... | high | medium | p1 | ... | ... | ... |

## Severity calibration

- Critical: could cause severe legal, financial, safety, security, or reputational harm.
- High: could materially harm users, customers, operations, trust, or cost profile.
- Medium: meaningful but controllable impact; likely manageable with normal controls.
- Low: minor impact or easily recoverable issue.

## Likelihood calibration

- High: likely under normal use or common adversarial behavior.
- Medium: plausible under realistic conditions.
- Low: edge case, requires unusual conditions, or has strong existing controls.
