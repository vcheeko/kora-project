# Security Policy

KORA is currently a **prototype-stage project**. This public repository does not contain the canonical private implementation, but responsible disclosure still matters.

## Reporting a security issue

Please **do not open a public GitHub issue** for a suspected vulnerability, credential exposure, sensitive configuration problem or exploitable security weakness.

Preferred path:

1. Use GitHub's **Private vulnerability reporting** for this repository if that option is available under the Security tab.
2. If it is not available, contact the founder through the public profile links in the README and request a private channel.
3. In the first message, describe the issue at a high level only. Do not send credentials, secrets, personal data or exploit material until a private channel is established.

## Helpful report contents

A useful report includes:

- affected public file, behavior or surface;
- impact you believe is possible;
- minimum steps needed to reproduce or understand the issue;
- whether the issue is already public;
- whether any credentials or personal data may have been exposed.

## Scope

Security-relevant reports may include:

- accidental publication of secrets or private material;
- repository configuration that could expose sensitive data;
- misleading security claims in public documentation;
- vulnerabilities in any future public KORA code or demo;
- unsafe defaults that could create material risk for users.

The private KORA implementation is not published here. Please do not attempt to obtain private systems, credentials or unpublished material without authorization.

## Current security posture

KORA should not currently be treated as:

- a production security boundary;
- a production sandbox;
- an enterprise-certified system;
- a general-purpose autonomous execution environment.

The bounded local execution bridge described in public documentation is a **prototype under staged testing**, not a claim of hardened isolation.

## Disclosure expectations

We ask reporters to allow reasonable time for assessment and remediation before public disclosure when a valid issue could create real risk.

We will prefer transparent acknowledgment once disclosure is safe, while avoiding publication of details that would unnecessarily expose users, systems or private implementation boundaries.
