---
name: write-user-story
description: "Create user stories and acceptance criteria from supplied, trusted requirements. Use for user-story drafting, not for reviewing or correcting the source requirements."
---

# User Story Writing

## Purpose

Transform supplied requirements into traceable user stories without reviewing or rewriting the source requirement set. Treat the requirements as correct.

## Inputs

Apply `.github/agent-rules/requirement-input-handling.md`. Use only supplied requirements and confirmed decisions.

## Workflow

1. Identify user roles, goals, expected value, behavior, conditions, and exceptions explicitly supported by the requirements.
2. Group requirements by a coherent user goal.
3. If a term or relationship is materially ambiguous and prevents a supported story, invoke `custom-ba-grilling` only for that ambiguity.
4. If information is absent rather than ambiguous, draft the supported portion and list it under `Missing Information`.
5. Write each story as `As a <role>, I want <capability>, so that <value>` only when all three elements are supported. Do not invent a role or value to complete the sentence.
6. Add observable acceptance criteria supported by the source. Use Given/When/Then where it improves clarity, but do not force it when a rule is clearer as a direct condition.
7. Trace every story and acceptance criterion to requirement identifiers or source locations.

## Output

1. `Result`
2. `Sources Used`
3. `User Stories`
4. `Acceptance Criteria`
5. `Traceability`
6. `Assumptions`
7. `Missing Information`
8. `Decision Log` when clarification occurred

## Constraints

- Do not review, correct, or challenge the supplied requirements.
- Do not invent actors, goals, benefits, behavior, or acceptance conditions.
- Do not invoke `custom-ba-grilling` solely because optional information is absent.
- Do not modify source documents.
