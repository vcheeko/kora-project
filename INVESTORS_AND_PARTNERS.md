# KORA — Investor / Partner Brief

## One sentence

KORA is building toward a **human-directed operating layer for reliable AI-assisted work**: natural-language control on top, persistent project state and risk-aware orchestration underneath, with verification before consequential outcomes are trusted.

## The problem

AI tools can already perform increasingly useful work, but multi-step projects still leave the user coordinating much of the system manually:

- reconstructing context;
- deciding what should happen next;
- choosing tools or agents;
- managing dependencies;
- controlling permissions and risk;
- checking whether execution really succeeded;
- recovering from failures;
- preventing concurrent work from creating conflicting state.

The KORA thesis is that **AI capability alone is not enough; reliable AI operations need an operating layer around that capability.**

## Product hypothesis

KORA should make it possible for a user to express intent in normal language while the system handles the operational layer:

```text
intent
→ project state
→ plan / dependencies
→ risk / authority
→ tool or agent execution
→ verification
→ persistent continuation
```

The human keeps authority over goals, scope and consequential approvals.

## What exists today

KORA is **pre-seed / prototype-stage**.

Private development has already implemented or substantially exercised:

- governance and human-authority concepts;
- controlled execution and fail-closed workflows;
- verification / review / evidence patterns;
- transaction-style execution semantics;
- natural-language continuation concepts;
- safe-parallelism rules;
- a bounded local execution bridge prototype exercised through staged local testing.

The public repository contains the project thesis, high-level architecture, milestone status and collaboration/diligence material while intentionally excluding private implementation and sensitive evidence.

There is **no claim of production readiness or validated product-market fit**.

## Why this may matter

The project is not betting that one specific model wins. The underlying hypothesis is that as model and tool capability improves, users and teams will still need a reliable way to manage:

- state;
- authority;
- dependencies;
- delegation;
- verification;
- recovery;
- continuation.

If that hypothesis is correct, KORA's value would sit **between human intent and changing model/tool capabilities**.

This is a hypothesis to validate, not a moat claim.

## Immediate milestone

The next target is a **minimal KORA Core**, not a broad platform.

It should prove one end-to-end loop:

```text
GOAL
→ PLAN
→ AUTHORIZED ACTION
→ EXECUTION
→ VERIFICATION
→ RECEIPT
→ PERSISTENT STATE
→ CONTINUE LATER
```

Then KORA should be tested on a real project against a simpler baseline: an AI assistant plus manual tool management.

## What the pilot should measure

- task completion rate;
- human coordination burden;
- number of unnecessary approvals/questions;
- failure detection;
- recovery quality;
- verification quality;
- context reconstruction avoided;
- time saved;
- new failure modes introduced by KORA itself.

## Founder profile

**Miha Tavčar — Ljubljana, Slovenia**

Miha is a systems/product-oriented founder. His strengths are product vision, structured problem decomposition, workflow/governance design, AI-assisted prototyping, testing and multilingual communication.

He is deliberately **not positioning himself as a senior software engineer**. A central near-term objective is to add strong technical leadership that can simplify, challenge and implement the system rigorously.

## What we are looking for now

### Technical co-founder / lead engineer

Highest priority. Strong backend/systems judgment, durable state, workflow engines, agent/tool execution, testing, observability and security thinking are especially relevant.

### Specialist collaborators

AI/agent engineering, reliability/security, evaluation and product/UX.

### Pilot partners and mentors

People or teams with a real multi-step workflow where reliability, handoffs, repeated context and tool coordination are painful enough to measure.

### Capital

We are open to **pre-seed investors and accelerators**, but the near-term goal is evidence, not fundraising theater.

#### Indicative next-stage capital plan

A current planning range for a focused next stage is approximately **€250k–€500k**, depending on team structure, partner involvement and the pace of the build. This is an **indicative planning range, not a formal investment offer**.

The purpose of that capital would be to fund roughly **12–18 months of evidence-building work** around a deliberately narrow objective: build the minimal KORA Core, put it into a controlled real-world pilot and determine whether the product thesis is strong enough to justify broader productization.

Early capital would primarily fund:

- technical co-founder / lead engineering capacity;
- backend and AI systems development;
- minimal KORA Core implementation;
- secure execution / sandbox and evaluation infrastructure;
- testing, observability and verification tooling;
- product UX and interface work;
- pilot implementation and user research;
- essential early legal and operational setup.

#### What that capital should unlock

The target outcome is not a large organization or premature scale. It is evidence:

1. a working persistent KORA Core;
2. one complete governed execution loop across sessions;
3. a controlled real-project pilot;
4. measurable comparison against a simpler AI-assistant + manual-tool baseline;
5. enough technical and user evidence to decide whether KORA should scale, change direction or stop.

## What we are not asking an investor to believe yet

We are not asking anyone to assume:

- production readiness;
- product-market fit;
- enterprise security certification;
- a proven moat;
- general autonomous execution.

The appropriate diligence question today is narrower:

> **Can KORA demonstrate a materially more reliable and lower-friction project workflow than using an AI assistant plus manual tool management?**

That is the evidence the next phase should produce.

## Public diligence links

- [Project Status & Roadmap](docs/STATUS_AND_ROADMAP.md)
- [High-Level Architecture](docs/ARCHITECTURE.md)
- [Design Principles](docs/DESIGN_PRINCIPLES.md)
- [FAQ](docs/FAQ.md)
- [Collaborate](COLLABORATE.md)
