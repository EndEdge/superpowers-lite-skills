---
name: requesting-code-review-lite
description: Request an independent review after substantial code changes or before delivery or merge. Use a reviewer sub-agent by default to check the implementation against requirements; use main-agent self-review only when the user explicitly permits skipping the sub-agent.
---

# Requesting Code Review Lite

Obtain an independent, evidence-based review of completed work before defects become part of the delivery.

## Reviewer selection

Use a reviewer sub-agent by default. The separation is intentional: the reviewer should evaluate the work product without inheriting the implementer's assumptions.

When the agent tool supports context control, create the reviewer with a fresh or no-history context and provide only the focused review packet below. Do not rely on the tool's default context behavior, because it may inherit the implementer's conversation. If full isolation is unavailable, still use the sub-agent but explicitly restrict its evaluation to the supplied requirements and artifacts.

The main agent may self-review only when the user explicitly says that a sub-agent is unnecessary or permits review without one. Do not infer permission from urgency, task size, or unavailable capacity.

If the environment cannot run a sub-agent, state that limitation and ask whether the user accepts a main-agent review. Do not silently downgrade.

## Prepare a focused review packet

Give the reviewer the minimum context needed to judge the work:

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

After fixes, rerun the smallest relevant checks and review the resulting diff. Request another independent pass when the fixes are substantial or alter the original design.
