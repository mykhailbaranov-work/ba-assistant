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

A release note subject is the exact functionality name, location, or application entry to use in one Release Note Description paragraph. Each subject has a subject type: `functionality` or `location`. For a single subject, use either the functionality value or the location value, not both.

If the requirements are absent, ask the user to provide them. If issue type or subject information is absent or ambiguous, ask a targeted question that lets the user choose one or more subjects. When requirements support both functionality and location candidates, present both sets and label each candidate with its subject type. Allow the user to provide custom subject values and require a subject type for each custom subject. Do not invoke `custom-ba-grilling`.

## Workflow

1. Inventory the supplied requirements and identify their source locations.
2. Collect any missing required input through focused questions, including one or more release note subjects when needed.
3. Read the guideline section for the confirmed issue type.
4. Extract only supported user-visible behavior, scope, conditions, and business value.
5. Write one Release Note using the required structure, selected subject values, and exact supplied terminology. Put multiple selected subjects into separate Description paragraphs within the same Release Note. Do not create separate Release Notes or separate Enhancement sections for multiple subjects.
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
- Do not output a separate subject type field in the final result.
- Do not modify source documents.
