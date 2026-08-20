# Contributing to KORA

Thank you for taking an interest in KORA.

This repository is currently a **public collaboration and diligence surface**, not the canonical engineering repository. The most useful contributions at this stage are focused, evidence-aware and compatible with that boundary.

## Useful contributions now

We welcome public contributions such as:

- architecture critique;
- design simplification proposals;
- evaluation methodology;
- failure-mode analysis;
- product / UX feedback;
- documentation corrections and improvements;
- pilot proposals;
- references to relevant technical approaches or prior art;
- bounded prototype ideas that can be discussed safely in public.

## What is not currently open for public contribution

The following are intentionally not maintained in this repository:

- canonical KORA implementation;
- private governance rule registers;
- internal execution scripts;
- credentials or environment configuration;
- exact security and approval boundaries;
- private verification/evidence artifacts;
- unpublished IP-sensitive implementation material.

Please do not ask maintainers to publish these solely to support a public contribution.

## Before opening an issue

A strong issue should answer:

1. **What problem are you addressing?**
2. **Why does it matter at KORA's current stage?**
3. **What is the smallest useful change or experiment?**
4. **How could we tell whether it worked?**
5. **What new complexity or risk would it introduce?**

Prefer a falsifiable proposal over a broad feature list.

## Architecture feedback

Architecture feedback is especially useful when it identifies one of these:

- unnecessary complexity;
- hidden coupling;
- weak state semantics;
- ambiguous authority;
- unverifiable execution;
- unsafe concurrency;
- poor recovery behavior;
- UX that exposes too much internal machinery;
- assumptions that should be tested before implementation.

## Pull requests

Public pull requests should normally be limited to files that already belong to this public surface, such as documentation and public project metadata.

Before preparing a larger change, open an issue first so the scope can be discussed without wasting work.

Keep pull requests:

- small;
- single-purpose;
- easy to review;
- free of confidential or proprietary material;
- explicit about what claim or behavior changes.

## No confidential submissions

Do not submit:

- passwords, API keys or tokens;
- private keys or certificates;
- personal data that is not necessary and authorized for publication;
- employer-confidential information;
- proprietary code you do not have rights to share;
- security-sensitive implementation details;
- third-party copyrighted material without permission.

If you discover a security issue, **do not open a public issue**. Follow [SECURITY.md](SECURITY.md).

## Licensing / IP

Publication of this repository does not by itself grant an open-source license to KORA material.

Unless a specific file or future release explicitly states otherwise, the terms in [NOTICE.md](NOTICE.md) apply.

If you want to contribute material for potential future incorporation into KORA, make sure you have the right to submit it. Questions about ownership or licensing should be resolved before substantial work is contributed.

## Collaboration beyond documentation

If you are interested in deeper technical collaboration, a pilot, advisory work or a founding role, see [COLLABORATE.md](COLLABORATE.md).
