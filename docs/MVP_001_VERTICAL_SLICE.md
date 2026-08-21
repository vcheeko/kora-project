# KORA MVP-001 — Vertical Slice

**Stage:** executable proof target  
**Public scope:** product behavior and measurable acceptance criteria only  
**Private scope:** internal governance rules, security boundaries, machine-specific execution details and evidence-chain internals remain private

## Objective

Prove one narrow claim:

> A user can state a concrete project goal in normal language and KORA can carry that goal through planning, bounded execution, verification and persistent continuation with materially less manual coordination than an AI assistant plus manual tool management.

MVP-001 deliberately avoids broad platform scope. It is one end-to-end loop, not a general autonomous agent system.

## Reference use case

**User goal:** “Create a simple professional website for a new project.”

The use case is intentionally familiar. The value under test is not website generation itself; it is whether KORA can manage the operational workflow around a multi-step task.

## End-to-end flow

```text
INPUT
→ UNDERSTAND
→ PLAN
→ EXECUTE
→ VERIFY
→ DECISION (only when needed)
→ RESULT
→ PERSIST
→ CONTINUE
```

### 1. INPUT
The user states the goal in normal language.

### 2. UNDERSTAND
KORA identifies the goal, known context, missing required information, constraints and an initial risk level. It asks only questions that block safe progress.

### 3. PLAN
KORA produces a bounded task plan with dependencies, expected outputs and verification points.

### 4. EXECUTE
KORA routes allowed actions to an appropriate tool or agent. Independent, reversible work may run concurrently; dependent or consequential work does not.

### 5. VERIFY
Important outputs are checked against explicit acceptance criteria. “The agent said it worked” is not sufficient verification.

### 6. DECISION
Human approval appears only when a consequential, irreversible, identity-changing, costly or otherwise gated action requires it.

### 7. RESULT
The user receives the result, verification status, remaining limitations and one clear next action.

### 8. PERSIST / CONTINUE
Project state is stored so the workflow can resume after interruption without reconstructing the project manually.

## Minimal user-facing state

The MVP should expose only five primary surfaces:

1. **What do you want to do?** — natural-language goal input.
2. **Current status** — one clear project state.
3. **What KORA is doing** — short human-readable activity, not raw logs.
4. **Need your decision** — visible only when required.
5. **Result** — output, verification and next step.

Technical detail such as model routing, logs, internal evidence and low-level tool activity should be progressively disclosed rather than permanently visible.

## Minimal internal state model

A project must be able to represent at least:

- project goal;
- task list;
- dependency relationships;
- task status: `planned`, `ready`, `running`, `blocked`, `needs_decision`, `verifying`, `done`, `failed`;
- authority/risk classification;
- action request;
- execution result;
- verification result;
- human decision when applicable;
- persistent continuation pointer / next valid action.

The public repository intentionally does not define private approval thresholds or security-sensitive implementation details.

## Acceptance criteria

MVP-001 passes only if one real test run can demonstrate all of the following:

- a user starts with a natural-language goal;
- KORA produces a bounded plan;
- at least two dependent steps are executed in valid order;
- at least one tool or agent action produces a real artifact/result;
- at least one output is independently verified against an acceptance criterion;
- the workflow can pause and resume from persistent state;
- a human decision gate is supported, even if the reference run does not require one;
- failures enter an explicit state rather than silently disappearing;
- the final user view clearly distinguishes `done`, `blocked`, `failed` and `needs_decision`;
- internal/private governance detail is not exposed in the public UX.

## A/B evaluation

Compare MVP-001 with a baseline workflow using an AI assistant plus manual tool management.

Measure:

| Metric | Baseline | KORA MVP-001 |
|---|---:|---:|
| User actions / handoffs | Measure | Measure |
| Copy/paste operations | Measure | Measure |
| Manual context reconstruction | Measure | Measure |
| Human decisions requested | Measure | Measure |
| Tool-selection decisions by user | Measure | Measure |
| Failed/retried steps | Measure | Measure |
| Verified outputs | Measure | Measure |
| Time to usable result | Measure | Measure |
| Resume-after-interruption effort | Measure | Measure |

The goal is not to force a win. If the KORA path adds more friction without measurable reliability benefit, the architecture should be simplified before scope expands.

## Out of scope for MVP-001

- general autonomous execution across arbitrary systems;
- production-grade enterprise permissions;
- broad plugin marketplace;
- full voice/phone product;
- multi-tenant deployment;
- comprehensive billing;
- polished analytics;
- claims of production readiness or product-market fit.

## Exit gate

MVP-001 is complete when the team can show a repeatable end-to-end run and answer, with measured evidence:

> Did KORA reduce coordination burden while preserving or improving verification, recovery and human authority?

If yes, the next step is a controlled real-project pilot. If no, simplify the core before adding features.
