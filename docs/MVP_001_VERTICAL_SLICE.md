# KORA MVP-001 — Vertical Slice

**Stage:** executable proof target  
**Public scope:** product behavior, test boundaries and measurable acceptance criteria only  
**Private scope:** internal governance rules, security boundaries, machine-specific execution details and evidence-chain internals remain private

## Objective

Prove one narrow claim:

> A user can state a concrete project goal in normal language and KORA can carry that goal through planning, bounded execution, human authority gates, verification and persistent continuation with materially less manual coordination than an AI assistant plus manual tool management.

MVP-001 is one end-to-end loop, not a general autonomous agent system.

## Reference use case

**User goal:** “Create a simple professional website for a new project.”

The use case is intentionally familiar. Website generation is not the product claim. The test is whether KORA can manage the operational workflow around a multi-step task.

## Correct end-to-end flow

```text
INPUT
→ UNDERSTAND
→ PLAN
→ SAFE EXECUTION
→ PRE-CHECK
→ DECISION / AUTHORITY GATE (only when required)
→ GATED ACTION (only after approval)
→ VERIFY
→ RESULT
→ PERSIST
→ CONTINUE
```

A gated action must never execute before the required human decision. If no gate is required, KORA proceeds from pre-check to verification without manufacturing an approval step.

### 1. INPUT
The user states the goal in normal language.

### 2. UNDERSTAND
KORA identifies the goal, known context, missing required information, constraints and an initial risk level. It asks only questions that block safe progress.

### 3. PLAN
KORA creates a bounded task plan with dependencies, expected outputs, authority boundaries and verification points.

### 4. SAFE EXECUTION
KORA routes allowed, reversible work to an appropriate tool or agent. Independent reversible work may run concurrently; dependent, canonical or consequential work does not.

For the reference use case, creating a local draft website is safe execution.

### 5. PRE-CHECK
Before a consequential action, KORA checks that prerequisites and the proposed result are ready enough to present a meaningful decision.

### 6. DECISION / AUTHORITY GATE
Human approval appears only when a consequential, irreversible, identity-changing, costly or otherwise gated action requires it.

For the reference use case, publishing the draft to a public surface is the example gated action.

### 7. GATED ACTION
Only an explicitly approved gated action may execute. Declining or withholding approval must leave the project in a safe, explainable state.

### 8. VERIFY
Important outputs are checked against explicit acceptance criteria after execution. “The agent said it worked” is not sufficient verification.

### 9. RESULT
The user receives the result, verification status, remaining limitations and one clear next action.

### 10. PERSIST / CONTINUE
Project state is stored so the workflow can resume after interruption without reconstructing the project manually.

## Minimal user-facing state

The MVP should expose only five primary surfaces:

1. **What do you want to do?** — natural-language goal input.
2. **Current status** — one clear project state.
3. **What KORA is doing** — short human-readable activity, not raw logs.
4. **Need your decision** — visible only when required.
5. **Result** — output, verification status and next step.

The user-facing state must make `done`, `blocked`, `failed` and `needs_decision` unambiguous. Technical detail such as model routing, raw logs, internal evidence and low-level tool activity should be progressively disclosed rather than permanently visible.

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
- receipts for state-changing actions;
- persistent continuation pointer / next valid action.

The public repository intentionally does not define private approval thresholds or security-sensitive implementation details.

## Public prototype claim boundary

The browser prototype in `prototype/index.html` is a **UX simulation**, not the executable KORA Core.

Therefore it must:

- label simulated checks as `DEMO` / `SIMULATED`, never as evidence of real execution;
- not imply that arbitrary natural-language input is already interpreted by a working engine;
- refuse or visibly block unsupported demo scenarios instead of silently running the website scenario for every input;
- demonstrate user-facing `needs_decision`, `blocked`, `failed` and `done` states without claiming production behavior.

A working MVP is reached only when the same flow is driven by persistent runtime state and real adapter/verifier results.

## Functional acceptance criteria

MVP-001 passes only if a real test suite demonstrates all of the following:

- a user starts with a natural-language goal;
- KORA produces a bounded plan;
- at least two dependent steps execute in valid order;
- at least one adapter action produces a real artifact/result;
- at least one output is checked by a verifier that does not merely trust the executor's success message;
- the workflow pauses and resumes from persisted state without manual context reconstruction;
- a gated action cannot execute before its required decision;
- a declined gate leaves a safe and explainable state;
- an injected execution or verification failure enters `failed` or `blocked` explicitly;
- the final user view clearly distinguishes `done`, `blocked`, `failed` and `needs_decision`;
- internal/private governance detail is not exposed in the public UX.

## Initial A/B evaluation protocol

Compare the same reference task using:

- **Baseline:** AI assistant + manual tool management.
- **KORA:** MVP-001 runtime + the same underlying task goal.

Run at least three comparable trials, including one interrupted/resumed run. Record raw counts before calculating the result.

| Metric | Initial MVP-001 pass condition |
|---|---|
| User coordination events: handoffs + copy/paste + manual tool-selection actions | Median at least **30% lower** than baseline |
| Manual context reconstruction after interruption | **0** reconstructed project-state steps in the KORA resume run |
| Resume effort | At most **1 user continuation action** after restart |
| Gated-action safety | **0** gated actions executed before required approval |
| Verification coverage | At least the same number of acceptance-critical outputs verified as baseline; never lower |
| Silent failures | **0**; injected failures become explicit `failed` or `blocked` state |
| Usable-result parity | KORA produces an artifact that satisfies the same reference acceptance criteria as baseline |
| Time to usable result | Record and compare; initial MVP may be up to **25% slower** if it meets all reliability/coordination gates above |

The 30% and 25% values are **initial falsifiable test thresholds**, not performance claims. They should be revised after real pilot data rather than tuned to force a win.

## Required evidence runs

Before MVP-001 is called complete, the implementation should pass at least:

1. **Happy path** — goal → draft artifact → optional gate → verification → persisted done state.
2. **Interrupted path** — stop after a persisted intermediate state, restart, and continue without rebuilding context manually.
3. **Failure path** — inject an adapter or verification failure and confirm explicit failure state with a valid continuation/recovery pointer.

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

MVP-001 is complete only when a repeatable runtime test can answer with measured evidence:

> Did KORA reduce coordination burden while preserving or improving verification, recovery and human authority?

If yes, the next step is a controlled real-project pilot. If no, simplify the core before adding features.
