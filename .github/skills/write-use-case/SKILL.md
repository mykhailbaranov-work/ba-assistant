---
name: write-use-case
description: "Write one or more use cases from supplied requirements using the project use-case guideline. Analyzes requirements first and preserves requirement traceability."
---

# Use Case Writing

## Mandatory Sources

Read and apply:

- `docs/use-case-writing-guideline.md`
- `.github/agent-rules/requirement-input-handling.md`

## Workflow

1. Require the source requirements. If none are supplied, ask the user to provide them.
2. Invoke `req-analyze` and use its functional grouping and extracted actors, triggers, inputs, actions, outputs, and exceptions.
3. Determine scope:
   - Write one use case when the requirements describe one shared goal and flow, even across several areas or screens.
   - If clearly unrelated functionality is present, ask whether to split it or keep one use case.
   - If the relationship is materially unclear, invoke `custom-ba-grilling` only to resolve the split or merge decision.
4. Draft only behavior supported by the analyzed requirements.
5. Apply the guideline's flow, numbering, and step-label rules.
6. List covered requirement identifiers or locations separately from the use-case prose.
7. Report unplaced requirements, conflicts, and missing information.

## Output per Use Case

1. `Name`
2. `Brief Description`
3. `Actors`
4. `Preconditions`
5. `Basic Flow`
6. `Alternative Flows` when applicable
7. `Exception Flows` when applicable
8. `Covered Requirements`
9. `Assumptions`
10. `Missing Information`

## Constraints

- Do not skip `req-analyze`.
- Do not invent actors, steps, conditions, or behavior.
- Do not place requirement identifiers inside the use-case narrative or flows.
- Do not silently decide to split or merge unrelated functionality.
- Do not modify source documents.
