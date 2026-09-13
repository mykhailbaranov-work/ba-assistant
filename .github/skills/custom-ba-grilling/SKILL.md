---
name: custom-ba-grilling
description: "Clarify material ambiguity in requirements through focused interview rounds. Use when another BA workflow explicitly calls for clarification before it can safely continue."
---

# Requirements Clarification Interview

## Purpose

Resolve missing decisions and material ambiguity without inventing business behavior. This skill clarifies requirements; it does not review their writing quality or produce the final deliverable owned by the calling skill.

## Inputs

Use the requirement text, supporting evidence, open questions, and prior decisions supplied by the calling workflow. Apply `.github/agent-rules/requirement-input-handling.md`.

## Workflow

1. State the feature, requirement set, or decision being clarified.
2. Summarize the current understanding in concrete points.
3. Identify the highest-risk unresolved information.
4. Ask one round of 3-7 focused questions. Include a recommended answer only when evidence supports it.
5. Wait for the user's answers before starting another round.
6. Update confirmed facts, decisions, assumptions, dependencies, and unresolved questions.
7. Record each question, answer, decision, affected requirement or source, and resulting change in a `Decision Log`.
8. Repeat only while a material ambiguity prevents the calling workflow from continuing.
9. Ask the user to confirm the consolidated understanding, then return a `Clarification Handoff` to the calling skill.

Cover terminology, goal, actors, triggers, inputs, actions, outputs, exceptions, permissions, lifecycle, dependencies, and acceptance conditions only where relevant.

## Missing References

If a requirement depends on unavailable requirement text, request the exact referenced content and mark dependency checks `Pending`. Do not infer it.

## Output

For each round provide:

1. `Current Understanding`
2. `Questions`
3. `Recommended Answers`
4. `Confirmed Decisions`
5. `Open Assumptions`
6. `Pending Dependencies`
7. `Decision Log`

The final `Clarification Handoff` contains confirmed terminology, behavior, decisions, acceptance conditions, dependencies, and unresolved questions.

## Constraints

- Do not finalize the calling workflow's deliverable.
- Do not invent or silently resolve business rules or source conflicts.
- Do not modify source documents.
- If the user stops the interview, return the unresolved points and only the explicitly confirmed assumptions.
