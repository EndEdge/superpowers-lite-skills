# Superpowers Lite Skills

Four small, standalone Codex skills adapted from selected workflows in [obra/superpowers](https://github.com/obra/superpowers):

- `brainstorming-lite` clarifies intent and obtains design approval before implementation.
- `requesting-code-review-lite` requests an independent sub-agent review by default.
- `receiving-code-review-lite` verifies review feedback before applying it.
- `systematic-debugging-lite` finds evidence-backed root causes before fixing failures.

Each directory is a complete skill, including a copy of the applicable MIT license. None of the skills depends on the Superpowers plugin, another skill in this repository, or repository-level runtime files.

## Install

Copy only the skill directories you want into your Codex skills directory. On Windows, the default user location is:

```text
%USERPROFILE%\.codex\skills\
```

For example, installing `brainstorming-lite` should produce:

```text
%USERPROFILE%\.codex\skills\brainstorming-lite\SKILL.md
```

Restart or refresh Codex if the new skill is not discovered immediately.

## Design goals

- Preserve the decision-making value of the original workflows.
- Remove plugin-specific orchestration and cross-skill dependencies.
- Keep process proportional to the task.
- Keep every skill independently understandable and installable.

The code-review requester uses a reviewer sub-agent by default. It permits main-agent self-review only when the user explicitly allows skipping the sub-agent.

## Attribution and license

These skills are rewritten and reduced derivatives of concepts and instructions from Superpowers by Jesse Vincent. The upstream project and this repository are licensed under the MIT License. See [LICENSE](LICENSE).
