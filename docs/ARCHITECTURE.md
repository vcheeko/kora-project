# KORA — High-Level Architecture

This document describes only the **public, non-sensitive architecture**. The canonical implementation, internal governance artifacts and exact security boundaries are intentionally not published here.

## System model

```text
┌───────────────────────────────────────────────────┐
│                      HUMAN                        │
│        goals • scope • approvals • decisions      │
└──────────────────────┬────────────────────────────┘
                       │ natural language
                       ▼
┌───────────────────────────────────────────────────┐
│                    KORA UX                        │
│     intent • status • explain • ask • continue    │
└──────────────────────┬────────────────────────────┘
                       ▼
┌───────────────────────────────────────────────────┐
│                   KORA CORE                       │
│                                                   │
│  Persistent State      Task / Dependency Model    │
│  Intent Interpretation Risk Classification        │
│  Authority Model       Tool / Agent Router        │
│  Checkpoints           Receipts / Evidence        │
│  Failure State         Recovery / Continuation    │
└───────────────┬──────────────────┬────────────────┘
                │                  │
                ▼                  ▼
        ┌───────────────┐   ┌───────────────┐
        │ Tools / APIs  │   │   AI Agents   │
        │ local / SaaS  │   │  specialists  │
        └───────┬───────┘   └───────┬───────┘
                └──────────┬─────────┘
                           ▼
┌───────────────────────────────────────────────────┐
│       VERIFY → RECEIPT → STATE UPDATE → NEXT      │
└───────────────────────────────────────────────────┘
```

## Responsibility by layer

### 1. Human

The human remains the highest project authority for:

- goals;
- scope;
- consequential approvals;
- irreversible or high-impact decisions;
- accepting or rejecting major changes.

KORA is designed to reduce coordination burden, not remove human responsibility.

### 2. KORA UX

The UX should translate ordinary language into structured project intent while hiding unnecessary orchestration detail.

The ideal interaction is not a command language. A user should be able to say things like:

- continue;
- show me where we are;
- do the next safe step;
- work on independent safe tasks in parallel;
- explain why this is blocked;
- stop and preserve state.

When intent is ambiguous in a way that matters, KORA should ask. When the next safe action is already clear, it should avoid unnecessary questioning.

### 3. KORA Core

The Core is responsible for turning intent into controlled project progress.

Key responsibilities:

- maintain durable project state;
- represent dependencies and blocked work;
- classify risk and required authority;
- select the next valid action;
- route work to tools or agents;
- prevent unsafe or conflicting parallel execution;
- require verification where consequences justify it;
- persist receipts and state transitions;
- expose failure and recovery states instead of silently continuing.

### 4. Tools and AI agents

Tools and agents are capabilities, not authorities.

KORA may delegate bounded work to them, but delegation should include enough context to define:

- the objective;
- allowed scope;
- authority;
- expected output;
- verification requirement;
- failure behavior.

An agent producing confident text is not itself proof that an action succeeded.

### 5. Verification and state update

A consequential action should not become trusted project state merely because execution was attempted.

The intended pattern is:

```text
REQUEST
  ↓
AUTHORITY / RISK CHECK
  ↓
EXECUTION
  ↓
VERIFICATION
  ↓
RECEIPT / EVIDENCE
  ↓
STATE TRANSITION
```

The strength of verification should scale with consequence, reversibility and uncertainty.

## Safe parallelism

KORA is being designed to distinguish between work that can safely happen at the same time and work that must remain sequential.

Good candidates for parallel work:

- independent research;
- reversible analysis;
- isolated drafting;
- read-only inspection;
- work whose outputs cannot mutate the same canonical state.

Poor candidates for parallel work:

- dependent gate transitions;
- identity-changing operations;
- destructive actions;
- competing writes to canonical state;
- verification chains where one result depends on the previous one.

Parallelism is a performance tool, not a reason to weaken state integrity.

## Trust boundaries

KORA's architecture assumes that different actions deserve different levels of trust.

A future implementation should distinguish at least:

- read-only vs. write actions;
- reversible vs. irreversible actions;
- local vs. external effects;
- low-impact vs. consequential decisions;
- deterministic checks vs. model judgments;
- human-approved vs. delegated authority.

The exact private authorization model is intentionally not published here.

## Current bridge prototype

Private development includes a **bounded local execution bridge prototype** intended to explore the transition from conversational instructions to controlled machine execution.

The public claim is deliberately limited: the prototype has been implemented and exercised through staged local testing. It is **not** presented as a production executor, secure sandbox or general autonomous runtime.

## Design questions still open

1. What is the smallest persistent state required for reliable continuation?
2. Which actions can be automated without creating approval fatigue or unacceptable risk?
3. How should governance depth scale with consequence and reversibility?
4. How should multiple agents coordinate without corrupting canonical state?
5. How can verification remain visible enough to earn trust without making the UX heavy?
6. Which parts of risk classification should be deterministic versus model-assisted?
7. What is the smallest real-world pilot that can falsify the KORA hypothesis?
8. When does voice/phone interaction become practical without reducing control or transparency?

## Deliberately not public here

- canonical governance rule registers;
- private execution scripts and source code;
- exact approval/security boundaries;
- internal evidence artifacts and hashes;
- credentials or machine-specific environment information;
- unpublished IP-sensitive implementation details.

For current milestone state, see [Project Status & Roadmap](STATUS_AND_ROADMAP.md).
