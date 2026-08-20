# KORA — Project Status & Roadmap

**Status date:** 20 August 2026  
**Stage:** pre-product / prototype-stage  
**Primary objective:** move from governed prototypes to a minimal end-to-end KORA Core and a real-project pilot.

## Current status at a glance

| Area | Current state | Public claim level |
|---|---|---|
| Project thesis / UX direction | Defined and actively refined | Public |
| Human authority / governance model | Substantially explored in private development | High-level only |
| Verification / evidence workflow | Implemented and exercised as prototype workflow | High-level only |
| Transaction semantics | Prototype model explored and tested | High-level only |
| Natural-language continuation | Working interaction concept | Public concept |
| Safe parallelism | Rules defined and exercised in governed workflow | High-level only |
| Local execution bridge | Bounded prototype implemented and exercised in staged local testing | High-level only |
| Persistent KORA Core | Not yet complete | Next milestone |
| End-to-end real-project pilot | Not yet complete | Planned |
| Product UX / voice-first interface | Vision defined, implementation later | Planned |
| Production readiness | **No** | Explicitly not claimed |
| Validated product-market fit | **No** | Explicitly not claimed |

## What has been completed or substantially explored

Private development has focused on the reliability layer that is easy to skip when building agent demos:

- versioned governance and human-authority concepts;
- controlled execution and fail-closed behavior;
- review, verification and evidence workflows;
- transaction-style request → authorization → execution → verification → state-update semantics;
- recovery-aware thinking and checkpoint concepts;
- natural-language continuation instead of rigid command memorization;
- safe-parallelism rules for independent, reversible work;
- a bounded local execution bridge prototype;
- repeated staged testing of project-state and execution workflows;
- separation between public collaboration material and private engineering evidence.

These items should be understood as **prototype/research engineering**, not as a finished platform.

## What is deliberately not claimed

KORA does not currently claim:

- production reliability;
- autonomous execution across arbitrary systems;
- complete security isolation;
- validated enterprise deployment;
- validated product-market fit;
- a finished developer platform;
- a complete voice/phone experience.

The project is intentionally publishing the **stage it is actually in**.

## Roadmap

### M1 — Public collaboration surface — **ACTIVE / substantially complete**

Purpose: make the project understandable without exposing private implementation.

Deliverables:

- clear README and project thesis;
- public high-level architecture;
- status and roadmap;
- collaboration path;
- investor / partner brief;
- contribution, security and IP boundary guidance.

Exit criterion: a technical reviewer, potential collaborator or investor can understand the project, current evidence and current gaps without a private briefing.

### M2 — Minimal KORA Core — **NEXT**

Build the smallest executable core containing:

- durable project state;
- task/dependency representation;
- intent classification;
- risk/authority model;
- action/checkpoint/receipt format;
- minimal tool/agent router;
- explicit failure and recovery states.

Exit criterion: KORA can persist one project's state and select the next valid action deterministically enough to test.

### M3 — End-to-end execution loop

Demonstrate one complete project loop:

```text
Human goal
→ plan
→ dependency/risk check
→ authorized tool or agent action
→ verification
→ receipt
→ persistent state update
→ reliable continuation
```

Exit criterion: the loop survives interruption and can continue later without reconstructing the project manually.

### M4 — Real-project pilot

Use KORA on a real project rather than continuing to improve KORA only in isolation.

Measure:

- task completion rate;
- number and quality of human interventions;
- recovery from failures;
- verification quality;
- context reconstruction avoided;
- time saved;
- unnecessary governance overhead;
- failure modes that KORA introduces itself.

Exit criterion: enough evidence exists to decide whether the KORA approach materially improves the workflow.

### M5 — Product UX

Only after the core loop earns evidence:

- simple status / dashboard;
- conversational control;
- mobile-friendly experience;
- later, voice / phone as a primary control surface;
- progressive disclosure of technical detail.

## The next falsifiable question

The project should now try to answer one question rather than add more conceptual scope:

> **Can a minimal KORA Core manage a real multi-step project with less coordination burden and better recovery/verification than an AI assistant plus manual tool management?**

If the answer is no, the architecture should change before the scope grows.

## Public evidence policy

The public repository reports **capability level and milestone state**, not private operational evidence.

We intentionally do not publish:

- machine paths;
- internal hashes or evidence-chain identifiers;
- private source code;
- credentials or environment details;
- exact security/approval boundaries;
- unpublished implementation IP.

This keeps the public status useful for diligence without turning the showcase repository into the canonical engineering system.
