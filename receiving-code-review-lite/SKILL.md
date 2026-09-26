---
name: receiving-code-review-lite
description: Evaluate code review feedback against the current code, requirements, and compatibility constraints before implementing it. Use when review comments are received, especially when they are ambiguous, broad, or technically questionable.
---

# Receiving Code Review Lite

Treat review feedback as technical input to verify, not instructions to accept automatically.

## Understand the feedback

Read the complete review and group related comments. For each item, identify:

- the behavior or risk the reviewer believes is wrong;
- the requested change, if one is stated;
- the evidence or assumption behind the claim;
- whether it conflicts with another comment or an approved decision.

If ambiguity would change the implementation, clarify it before modifying the affected behavior. Do not guess at a requirement or implement only the easy part of a coupled set of comments.

## Verify against the codebase

Inspect the cited code and surrounding flow. Check:

- whether the reported path is reachable;
- whether existing tests, callers, and platform constraints support the claim;
- why the current implementation exists;
- whether the proposed change breaks compatibility or approved behavior;
- whether the suggested feature has an actual consumer.

Feedback from the user is authoritative about intent, but scope may still need clarification. Feedback from automated or external reviewers requires the same technical verification as any other hypothesis.

## Decide and respond

For each item, choose one outcome:

- **Accept:** the issue is valid and the proposed direction fits the requirements.
- **Adapt:** the issue is valid, but a different change addresses it more safely.
- **Reject:** the claim is unsupported, incompatible, out of scope, or unnecessary.
- **Clarify:** available information is insufficient to choose safely.

State the technical conclusion concisely. When rejecting or adapting a suggestion, cite code behavior, requirements, or verification evidence. Escalate conflicts with an approved architecture or product decision to the user.

## Apply accepted changes

Order work by dependency and risk: blockers and correctness issues first, then independent small fixes, then larger refactors. Keep each change focused and run proportionate checks after it so failures can be attributed to a specific modification.

Before declaring the review resolved, confirm that:

- every actionable comment has a recorded outcome;
- accepted issues are fixed and relevant checks pass;
- rejected items have evidence-based reasoning;
- no unrelated feature or refactor was added.
