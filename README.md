# KORA

**A human-directed operating layer for reliable AI-assisted work.**

KORA is an early-stage project exploring how a person can work with AI through natural language while the system handles project state, task dependencies, risk, tools/agents, verification and evidence behind the scenes.

The goal is simple to describe:

> The human states the goal. KORA keeps the work organized, chooses the next safe action, coordinates tools or agents, verifies outcomes, and preserves enough state to continue reliably later.

## Why this exists

Today, advanced AI workflows often require the user to manually manage prompts, agent roles, repositories, context, approvals and recovery. KORA is being designed to reduce that operational burden without removing human authority.

## Core principles

- **Human-directed:** the human owns goals, scope and consequential approvals.
- **Intent-first UX:** natural language should replace memorized command syntax wherever possible.
- **Risk-proportional governance:** low-risk work stays lightweight; consequential work receives stronger checks.
- **Persistent project state:** the system should know what is done, active, blocked and next.
- **Verification before trust:** important changes should produce evidence, not just confident text.
- **Safe autonomy:** agents/tools may act independently only inside defined authority and recovery boundaries.
- **Private implementation, public collaboration layer:** sensitive implementation and governance evidence remain private while this repository explains the project and collaboration opportunities.

## High-level flow

```text
Human goal
   ↓
KORA intent + project state
   ↓
Plan / dependencies / risk
   ↓
Tool & agent orchestration
   ↓
Execution
   ↓
Verification / evidence
   ↓
Persistent state + next action
```

## Current stage

KORA is **pre-product / prototype-stage infrastructure work**, not a finished autonomous assistant. Private development has focused on governance rules, controlled execution, verification, transaction semantics and a local bridge concept. The next major milestone is a small end-to-end KORA Core that can manage a real project loop with persistent state.

See [Project Status & Roadmap](docs/STATUS_AND_ROADMAP.md).

## We are looking for

- a **technical co-founder / lead engineer** who enjoys AI systems, orchestration and product architecture;
- **AI/backend engineers** interested in agent workflows, persistent state, tool execution and evaluation;
- **security / reliability collaborators** interested in sandboxing, permissions, recovery and auditability;
- **product/UX collaborators** interested in making powerful AI systems usable through simple natural-language interaction;
- **early partners, mentors and investors** who understand pre-seed AI infrastructure / productivity systems.

See [Collaborate](COLLABORATE.md) and [Investor / Partner Brief](INVESTORS_AND_PARTNERS.md).

## Founder

**Miha Tavčar — Ljubljana, Slovenia**  
GitHub: `@vcheeko`  
LinkedIn: `miha-tavcar-773502101`

Miha's role is product vision, systems thinking, workflow/governance design, AI-assisted prototyping, testing and project direction. He is **not presented as a senior software engineer**; one purpose of this public collaboration effort is to build a technically strong founding/collaboration team around the project.

## Important note

This public repository is intentionally a **showcase and collaboration surface**, not the canonical private engineering repository. It does not publish private source code, credentials, internal evidence chains, sensitive operational details or security boundaries.

Unless explicitly licensed otherwise, publication here does **not** grant permission to copy or commercialize private KORA implementation or project IP. See [NOTICE](NOTICE.md).
