---
name: requesting-code-review-lite
description: Review completed code changes against requirements after substantial changes, before delivery or merge, or when the user requests review. The main agent may self-review; delegate to a reviewer sub-agent only when the user explicitly requests review and has not prohibited sub-agents.
---

# Requesting Code Review Lite

Perform an evidence-based review of completed work before defects become part of the delivery.

## Reviewer selection

The main agent may review the work directly without asking for permission to self-review. Routine development, fixes, validation, delivery, merge preparation, and automatic selection of this skill do not authorize spawning a reviewer sub-agent.

Spawn a reviewer sub-agent only when the user explicitly requests review of the work, such as "review these changes" or "帮我 review 一下", and has not instructed you to review directly or avoid sub-agents. An explicit review request permits delegation; it does not require it. A request to edit this skill or a review-related document is not a request to review the implementation.

When delegation is authorized and chosen, create the reviewer with a fresh or no-history context if the agent tool supports context control, and provide only the focused review packet below. Do not rely on the tool's default context behavior, because it may inherit the implementer's conversation. If full isolation is unavailable, explicitly restrict the reviewer's evaluation to the supplied requirements and artifacts.

If sub-agents are unavailable, review directly unless the user specifically requires an independent or sub-agent review. In that case, report the limitation. Describe main-agent review as self-review, not independent review.

## Prepare a focused review packet

For self-review, inspect the evidence below directly. When delegating, give the reviewer the minimum context needed to judge the work:

- the requested outcome and acceptance criteria;
- explicit constraints and exclusions;
- a concise description of the implementation;
- the changed files or diff;
- a base and head revision when available;
- tests or checks already run and their results;
- known limitations that remain in scope.

Do not send unrelated session history or tell the reviewer which conclusion to reach.

Use a prompt with this shape:

```text
Review this change against the supplied requirements.

Requirements:
<requirements and constraints>

Implementation:
<summary and changed scope>

Evidence:
<diff or revisions, plus completed checks>

Report only actionable findings. For each finding, give severity,
location, technical impact, and supporting reasoning. Note any
requirement that cannot be verified from the available evidence.
```

## Evaluate the result

Check every finding against the actual code and requirements before acting on it. Classify findings as:

- **Critical:** security, data loss, broken core behavior, or a delivery blocker;
- **Important:** incorrect behavior, meaningful regression, or an unmet requirement;
- **Minor:** maintainability or clarity improvement that does not block delivery.

Fix valid Critical and Important findings before delivery. If a finding is incorrect, explain why using code, requirements, or verification evidence. Record Minor findings only when they are genuinely useful; do not expand scope merely to satisfy a reviewer.

After fixes, rerun the smallest relevant checks and review the resulting diff. Substantial fixes or design changes do not independently authorize delegation: apply the same reviewer-selection rule to any follow-up pass and keep it within the user's requested review scope.
