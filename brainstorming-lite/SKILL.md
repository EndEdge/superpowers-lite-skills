---
name: brainstorming-lite
description: Clarify intent and produce a proportionate, user-approved design before creating features, components, or behavior changes. Use when implementation involves product or technical choices; skip purely mechanical edits with no meaningful design decision.
---

# Brainstorming Lite

Turn an implementation idea into a shared design without imposing a heavyweight planning system.

## Establish the brief

Inspect relevant existing files and documentation before proposing changes. Identify:

- the outcome the user wants;
- who or what the change serves;
- constraints and explicit exclusions;
- observable success criteria.

Separate facts supplied by the user from assumptions. If a missing answer would materially change the result, ask one focused question at a time. Do not repeat questions already answered by the request or repository context.

Reflect the brief back concisely so the user can correct it.

## Match design depth to the change

Use the lightest design that makes the important decisions explicit:

- For a contained change to an existing flow, present a short in-chat design covering the approach, affected areas, and verification.
- For a new project, subsystem, public interface, or cross-component change, explore the system boundaries and present a structured design covering components, data flow, failure handling, migration or compatibility concerns, and verification.
- For a feasibility probe whose output is knowledge rather than retained code, state the question, probe, limits, and success signal.

Do not create a specification file or implementation plan unless the user requests one or the project requires it.

## Explore real choices

When multiple approaches have meaningful trade-offs, present two or three. Lead with the recommended option and explain why it best fits the brief. Remove speculative features and unrelated refactoring.

For existing codebases, follow established patterns unless changing them is necessary for the requested outcome. Include only targeted cleanup required to make the change safe or understandable.

## Approval gate

Before writing implementation code, scaffolding a new project, installing product dependencies, or making an external change:

1. present the proposed design at the appropriate depth;
2. identify any remaining assumptions;
3. ask the user to approve or correct it;
4. wait for approval.

Read-only exploration is allowed before approval. Approval applies to the design that was actually presented. If implementation reveals a materially different scope, architecture, risk, or user-facing behavior, stop and obtain approval for the revised design.

After approval, continue through the project's normal implementation workflow. This skill does not require any particular planning, testing, or execution skill.
