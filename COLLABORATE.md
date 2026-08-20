# Collaborate on KORA

KORA is looking for people who want to shape an early AI systems project, not simply receive a fixed list of tickets.

The project is still at the stage where **good technical judgment can materially change the architecture**.

## Highest-priority need

### Technical Co-Founder / Lead Engineer

Ideal background:

- strong backend / systems engineering;
- Python and/or TypeScript;
- LLM / agent / tool-calling systems;
- async jobs, queues, state machines or workflow engines;
- databases and durable state;
- testing, observability and failure recovery;
- security boundaries / sandboxing;
- willingness to remove unnecessary complexity rather than defend it.

The most important skill is the ability to turn a broad system concept into a **small, testable implementation with clear failure modes**.

## Other high-value collaborators

### AI / Agent Engineer

Focus:

- orchestration;
- tool execution;
- model routing;
- evaluation;
- context and state management.

### Reliability / Security Engineer

Focus:

- permissions;
- sandboxing;
- checkpoints;
- recovery;
- evidence;
- safe autonomy;
- threat and failure modeling.

### Product / UX Designer

Focus:

- simple conversational interaction;
- status and next-action clarity;
- progressive disclosure;
- mobile and later voice-first control;
- reducing approval and orchestration friction without hiding consequential decisions.

### Research / Evaluation Collaborator

Focus:

- test design;
- comparative baselines;
- failure taxonomies;
- reliability metrics;
- evaluation of human coordination burden.

### Pilot Partner

A useful pilot partner has a real workflow with several of these characteristics:

- repeated multi-step work;
- multiple tools or agents;
- state that must survive across sessions;
- handoffs or dependencies;
- meaningful verification requirements;
- recoverable but costly failures;
- enough repetition to compare KORA with a simpler baseline.

## How collaboration should start

We prefer a bounded trial before any long-term commitment:

1. 30–45 minute technical/product conversation;
2. choose one small architecture, evaluation or prototype problem;
3. define the expected output and boundaries;
4. work together for a short, defined period;
5. review judgment, communication and output quality;
6. only then discuss a deeper co-founder, equity, paid or advisory relationship.

No one should commit equity, money or a major role based on a pitch alone.

## Good first technical discussion topics

- minimal persistent-state schema;
- task/dependency representation;
- deterministic vs. model-assisted risk classification;
- agent/tool permission model;
- reversible execution and checkpoint strategy;
- verification and receipt design;
- what **not** to build in v0;
- the smallest real-world pilot that can falsify the concept.

## What can be shared publicly

This repository is suitable for:

- architecture critique;
- product and UX feedback;
- evaluation ideas;
- public documentation improvements;
- collaboration proposals;
- pilot proposals.

The canonical implementation and detailed governance/security evidence remain private.

Please read [CONTRIBUTING.md](CONTRIBUTING.md) and [NOTICE.md](NOTICE.md) before submitting material.

## Contact

Open a GitHub issue titled:

`COLLABORATION — <your area>`

Include:

- who you are;
- 2–3 relevant things you have built, researched or operated;
- what part of KORA interests you;
- what you would challenge or simplify first;
- whether you are exploring, contributing part-time, proposing a pilot or considering a founding role.

Do **not** put confidential information, proprietary employer material, credentials, personal data or security-sensitive details in a public issue.

For sensitive security reports, follow [SECURITY.md](SECURITY.md).
