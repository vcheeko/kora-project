# KORA — High-Level Architecture

This document intentionally describes only the public, non-sensitive architecture.

```text
┌─────────────────────────────────────────────┐
│                  HUMAN                      │
│        goals • approvals • decisions        │
└─────────────────────┬───────────────────────┘
                      │ natural language
                      ▼
┌─────────────────────────────────────────────┐
│                 KORA UX                     │
│     intent • status • explain • continue    │
└─────────────────────┬───────────────────────┘
                      ▼
┌─────────────────────────────────────────────┐
│               KORA CORE                     │
│                                             │
│  Project State       Task / Dependency      │
│  Intent Engine       Risk Classification    │
│  Authority           Agent / Tool Router    │
│  Checkpoints         Receipts / Evidence    │
└───────────────┬─────────────────┬───────────┘
                │                 │
                ▼                 ▼
        ┌──────────────┐   ┌──────────────┐
        │ Tools / APIs │   │ AI Agents    │
        │ local / SaaS │   │ specialists │
        └──────┬───────┘   └──────┬───────┘
               └──────────┬────────┘
                          ▼
┌─────────────────────────────────────────────┐
│       VERIFY → RECEIPT → STATE UPDATE       │
└─────────────────────────────────────────────┘
```

## Design questions we are actively testing

1. How much project state must be persisted for reliable continuation?
2. Which actions can be safely automated without human approval?
3. How should governance depth scale with consequence and reversibility?
4. How can multiple agents work in parallel without corrupting canonical state?
5. How do we make verification visible enough to earn trust but invisible enough to keep the UX simple?
6. How can a phone/voice interface eventually become a practical primary control surface?

## Deliberately not public here

- canonical governance rule register;
- private execution scripts and implementation details;
- exact approval/security boundaries;
- internal evidence artifacts and hashes;
- credentials, environment information or machine-specific paths;
- unpublished IP-sensitive implementation details.
