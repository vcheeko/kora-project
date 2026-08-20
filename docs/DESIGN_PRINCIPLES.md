# KORA — Design Principles

These principles describe the direction KORA is being designed around. They are not a claim that every principle is fully implemented today.

## 1. Human authority is explicit

The human owns goals, scope and consequential approvals.

Agents and tools may receive delegated authority, but they do not become the final project authority simply because they can act.

## 2. Intent before command syntax

Users should not need to memorize a control language for ordinary work.

KORA should infer normal continuation intent where context is sufficient and ask only when ambiguity materially affects scope, authority, risk or outcome.

## 3. State is a first-class system component

Reliable continuation requires more than chat history.

KORA should preserve enough structured state to know:

- what the goal is;
- what is done;
- what is active;
- what is blocked;
- what depends on what;
- what has been verified;
- what the next valid action is.

## 4. Verification before trust

Execution attempts and model confidence are not proof of success.

Important state transitions should be supported by proportionate verification or evidence.

## 5. Governance scales with consequence

Not every action deserves the same process.

Low-risk, reversible work should remain lightweight. Higher-impact, irreversible or uncertain work should receive stronger checks, clearer authority and better evidence.

The goal is **risk-proportional control**, not maximum process.

## 6. Safe autonomy is bounded autonomy

Automation is useful when its authority, scope and recovery path are understood.

KORA should prefer autonomy for work that is:

- well-scoped;
- low consequence;
- reversible;
- independently verifiable;
- unlikely to conflict with canonical state.

## 7. Parallelism must preserve state integrity

Independent safe work can happen in parallel.

Dependent gates, competing writes, destructive operations and verification chains should remain sequential unless a stronger coordination mechanism proves otherwise.

Speed is not worth corrupting project truth.

## 8. Failures are state, not noise

A failed action should become visible project state.

KORA should avoid silently skipping failures, fabricating completion or continuing as if a required step succeeded.

Failure handling should make recovery possible without rebuilding the entire project context.

## 9. Ask only when necessary

Questions are valuable when human information or approval is genuinely required.

Unnecessary clarification interrupts flow and transfers operational burden back to the user.

A good KORA interaction should distinguish between:

- ambiguity that can be safely resolved from context;
- ambiguity that changes consequences and requires the human.

## 10. Simplicity is a system requirement

Internal sophistication is only useful if it reduces the user's burden.

The external experience should aim to make powerful workflows understandable through a small number of concepts:

- where we are;
- what happened;
- what is next;
- what is blocked;
- what needs the human.

## 11. Claims must match evidence

Prototype work should be described as prototype work.

Research concepts, implemented prototypes, tested capabilities and production systems are different evidence levels and should not be presented as interchangeable.

## 12. Build the smallest falsifiable core first

KORA should not become an architecture project that endlessly expands its own scope.

The next implementation should be the smallest system capable of testing whether KORA actually improves a real workflow compared with a simpler baseline.
