---
name: req-write
description: "Write, rewrite, refine, or structure business, user, and functional requirements from supplied evidence. Uses clarification when needed and performs its own non-interactive quality check."
---

# Requirements Writing

## Purpose

Create clear, complete, consistent, verifiable, and traceable requirements without invoking the interactive `req-review` workflow.

## Mandatory Sources

Read and apply:

- `docs/requirements-writing-guideline.md`
- `.github/agent-rules/requirement-input-handling.md`
- `.github/agent-rules/source-selection.md`

## Workflow

1. Identify the objective, scope, stakeholders, affected systems, and expected outcome supported by the input.
2. Inventory the requirement inputs and supporting evidence.
3. Separate current behavior, proposed behavior, facts, rules, constraints, decisions, assumptions, and open questions.
4. Identify source conflicts and material gaps.
5. Invoke `custom-ba-grilling` before drafting when terminology, behavior, dependencies, exceptions, scope, or acceptance conditions are materially unclear.
6. Draft requirements without adding unsupported behavior or implementation details.
7. Preserve traceability from each requirement to its source statements and confirmed decisions.
8. Perform a non-interactive quality check of every drafted requirement against `docs/requirements-writing-guideline.md`.
9. Correct quality defects that do not require a new business decision. Return to `custom-ba-grilling` if correction would require one.
10. Present the resulting requirement set and any unresolved information.
11. If the primary source is a file below `source/`, use `document-output` and `.github/skills/req-write/assets/prepared-requirements-template.md` to create the prepared requirements automatically under `results/prepared_requirements_docs/`, preserving the source file's relative parent directory.
12. For chat or attachment input, create a prepared-requirements file only when the user requests one.

When rewriting existing requirements, preserve each original requirement and show proposed changes as full-text diffs.

## Output

1. `Result`
2. `Sources Used`
3. `Requirement Set`
4. `Traceability`
5. `Quality Check`
6. `Proposed Revisions` when rewriting supplied requirements
7. `Assumptions`
8. `Missing Information`
9. `Risks and Contradictions`
10. `Decision Log` when clarification occurred
11. `Created File` when a result file was produced

## Constraints

- Do not invoke `req-review`.
- Do not present assumptions or interpretations as approved requirements.
- Do not claim conformance when the mandatory writing reference was unavailable.
- Do not modify source documents.
- Do not overwrite or delete existing result files automatically.
