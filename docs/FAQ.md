# KORA — FAQ

## What is KORA?

KORA is an early-stage project exploring a **human-directed operating layer for reliable AI-assisted work**.

The goal is to let a person express intent in normal language while KORA manages project state, dependencies, bounded delegation, verification, recovery and continuation behind the scenes.

## Is KORA an AI model?

No.

KORA is intended to sit **around** models, agents, tools and APIs. The architecture should be able to evolve as those underlying capabilities change.

## Is KORA an autonomous agent?

Not in the simple sense.

KORA may delegate bounded work to agents or tools, but the design explicitly separates **capability** from **authority**. Human approval remains required where consequence, irreversibility or uncertainty justifies it.

## Is KORA production-ready?

No.

KORA is currently pre-product / prototype-stage. Some governance, verification, transaction and local execution-bridge concepts have been implemented or exercised in private development, but the minimal persistent end-to-end KORA Core is the next major milestone.

## What exists today versus what is still conceptual?

See [Project Status & Roadmap](STATUS_AND_ROADMAP.md) for the current evidence level by area.

In short:

- public project thesis and architecture: **exists**;
- private governance and verification prototypes: **substantially explored / exercised**;
- bounded local execution bridge prototype: **implemented and exercised in staged local testing**;
- minimal persistent KORA Core: **not yet complete**;
- real-project end-to-end pilot: **not yet complete**;
- production platform: **not claimed**.

## Why not just use ChatGPT, Claude, Gemini, Codex, Cursor or another agent product directly?

KORA is not based on the assumption that existing AI products are weak.

The hypothesis is that as models and agents become more capable, users still need a reliable operational layer for:

- durable project state;
- dependencies;
- authority;
- delegation;
- verification;
- recovery;
- continuation across sessions and tools.

The planned pilot should test whether that layer produces enough improvement to justify its own complexity.

## Is KORA a workflow engine?

Partly, but the intended scope is broader than a traditional fixed workflow engine.

KORA is exploring the intersection of:

- project state;
- workflow/dependency execution;
- human authority;
- natural-language intent;
- AI/tool orchestration;
- evidence and recovery.

A future implementation may reuse existing workflow-engine patterns rather than reinventing them.

## What is the local execution bridge?

Private development includes a bounded prototype that explores how conversational intent can be translated into controlled local machine execution.

The public claim is intentionally narrow: it has been implemented and exercised through staged local testing. It is not presented as a hardened sandbox, production executor or general autonomous runtime.

## Why is the implementation private?

The current public repository is designed for collaboration and diligence while KORA is still early.

It intentionally avoids publishing:

- security-sensitive boundaries;
- private execution code;
- internal evidence chains;
- credentials and environment details;
- unpublished IP-sensitive implementation.

This separation can change later if specific components are deliberately released under explicit terms.

## Is KORA open source?

Not currently as a whole.

Publication of this repository does not itself grant an open-source license. See [NOTICE](../NOTICE.md).

## What is potentially defensible about KORA?

That is still an open question.

The project should not claim a moat before it has a working core and pilot evidence. Potential value may come from the combination of state, authority, verification, recovery and low-friction UX, but the next job is to prove usefulness before making stronger defensibility claims.

## Who is KORA for?

The broad vision is non-technical or technical users who need AI to help execute real multi-step work without manually managing every piece of orchestration.

The first pilot should be narrower: one workflow with enough complexity, repetition and failure cost to measure whether KORA helps.

## Why emphasize governance so much?

Because more autonomous capability creates operational risk if state, authority and verification are vague.

But KORA is not trying to add heavyweight process everywhere. The design principle is **risk-proportional governance**: lightweight for safe, reversible work; stronger checks for consequential work.

## What would make KORA fail as a product idea?

Examples include:

- modern assistants already solve the coordination problem well enough;
- KORA adds more friction than it removes;
- persistent state is too brittle or expensive to maintain;
- verification costs exceed the value it adds;
- users do not trust or understand delegated authority;
- the architecture becomes too complex to operate reliably.

The real-project pilot should actively look for these failure modes rather than avoid them.

## What is the immediate next step?

Build the smallest persistent KORA Core capable of completing one end-to-end governed project loop, then compare it with a simpler baseline on a real workflow.

## How can I get involved?

See [Collaborate](../COLLABORATE.md) for technical, pilot, mentor and founding-role paths.
