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
- the exact name of the expanded functionality or application entry, or its applicable location/submenu.

If the requirements are absent, ask the user to provide them. If issue type or entry information is absent, ask a targeted question for that value. Do not invoke `custom-ba-grilling`.

## Workflow

1. Inventory the supplied requirements and identify their source locations.
2. Collect any missing required input through focused questions.
3. Read the guideline section for the confirmed issue type.
4. Extract only supported user-visible behavior, scope, conditions, and business value.
5. Write the Release Note using the required structure and exact supplied terminology.
6. Check the draft against every supplied requirement and identify any requirement that cannot be represented safely.

## Output

When inputs are sufficient:

1. `Release Note`
2. `Issue Type`
3. `Expanded Functionality or Entry`
4. `Sources Used`
5. `Assumptions`
6. `Missing Information`

When required inputs remain unavailable, return only `Information Needed` and `Reason`.

## Constraints

- Do not invoke `custom-ba-grilling`.
- Do not invent benefits, navigation paths, names, permissions, or delivered behavior.
- Do not finalize without requirements, issue type, and the expanded functionality or entry information.
- Do not modify source documents.
