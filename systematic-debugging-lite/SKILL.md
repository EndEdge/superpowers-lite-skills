---
name: systematic-debugging-lite
description: Investigate bugs, failing tests, build failures, and other unexpected technical behavior by gathering evidence and confirming a root cause before implementing a fix.
---

# Systematic Debugging Lite

Find and verify the cause of a failure before changing production code. The depth of investigation should match the impact and complexity of the issue.

## Establish the failure

Start with evidence:

1. Read the complete error, stack trace, warning, and relevant logs.
2. Record the exact failing command or reproduction steps and the expected result.
3. Determine whether the failure is consistent. If it is intermittent, capture the conditions that differ instead of guessing.
4. Inspect recent code, dependency, configuration, and environment changes that could affect the path.

Do not propose a fix merely because an error message resembles a familiar problem.

## Locate the cause

Trace the bad state backward to where it first becomes incorrect. In a multi-component flow, inspect boundaries such as client to API, workflow to build script, service to database, or cache to renderer. Capture inputs, outputs, configuration, and state at the narrowest useful points without exposing secrets.

Find a comparable working path in the same codebase when one exists. Compare all relevant differences before deciding which one matters, including data, ordering, platform, versions, state, and configuration.

State a single falsifiable hypothesis:

```text
The failure is caused by <specific condition> because <observed evidence>.
If that is true, <minimal check> will produce <expected result>.
```

Test one variable at a time with the smallest safe experiment. If the result disproves the hypothesis, discard it and form a new one from the updated evidence; do not stack speculative fixes.

## Implement and verify

Once evidence supports a root cause:

- add or reuse the smallest focused regression check that proves the final intended behavior when such a check is practical;
- make one targeted fix at the source of the problem;
- rerun the reproduction and the smallest relevant regression suite;
- inspect the final diff for symptom patches or unrelated cleanup.

Tests must validate the current approved design, not transitional code or an architecture scheduled for removal. Do not introduce performance baselines, benchmarks, profiling, long-running tests, repeated sampling, device matrices, or large workloads unless the user explicitly requests that exact evaluation.

If several distinct hypotheses fail, return to evidence collection. When repeated attempts expose shared-state or coupling failures in different areas, stop adding patches and discuss whether the architecture is the real problem.

If the cause is external or environment-dependent, document what was verified and implement only proportionate handling such as a bounded retry, timeout, or actionable error. Do not label a cause unknowable until the relevant boundaries have been investigated.
