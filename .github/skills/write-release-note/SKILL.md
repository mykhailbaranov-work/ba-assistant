---
name: write-release-note
description: "Write a Release Note from supplied requirements using the applicable issue-type section of the project guideline. Requests only missing mandatory inputs."
---

# Release Note Writing

## Mandatory Sources

Read and apply:

- the complete supplied requirement basis;
- the applicable issue-type section of `docs/release-note-writing-guideline.md`;
- `.github/agent-rules/requirement-input-handling.md`.

## Required Inputs

- issue type;
- complete requirements on which the note is based;
- one or more release note subjects.

A release note subject is the exact functionality name to use in the Release Note Description. Use a location or application entry as the subject only when the functionality cannot be inferred from the requirements.

If the requirements are absent, ask the user to provide them. If issue type or subject information is absent or ambiguous, ask a targeted question that lets the user choose one or more subjects. Suggest functionality-based subjects first. Suggest location-based subjects only when functionality-based subjects cannot be inferred. Allow the user to provide custom subject values. Do not invoke `custom-ba-grilling`.

## Workflow

1. Inventory the supplied requirements and identify their source locations.
2. Collect any missing required input through focused questions, including one or more release note subjects when needed.
3. Read the guideline section for the confirmed issue type.
4. Extract only supported user-visible behavior, scope, conditions, and business value.
5. Write the Release Note using the required structure, selected subject values, and exact supplied terminology.
6. Check the draft against every supplied requirement and identify any requirement that cannot be represented safely.

## Output

When inputs are sufficient:

1. `Release Note`
2. `Issue Type`
3. `Release Note Subject(s)`
4. `Sources Used`
5. `Assumptions`
6. `Missing Information`

When required inputs remain unavailable, return only `Information Needed` and `Reason`.

## Constraints

- Do not invoke `custom-ba-grilling`.
- Do not invent benefits, navigation paths, names, permissions, or delivered behavior.
- Do not finalize without requirements, issue type, and one or more release note subjects.
- Do not modify source documents.
