---
name: process-analyze
description: "Analyze a supplied current-state business process, identifying participants, steps, decisions, inputs, outputs, exceptions, and gaps. Does not design a target process."
---

# Current-State Process Analysis

## Purpose

Describe the supplied process as it currently operates. Make its sequence, decisions, responsibilities, inputs, outputs, exceptions, and observed gaps understandable without inventing a target state.

## Inputs

Use supplied process descriptions, requirements, diagrams, screenshots, and supporting evidence. When requirement text is included, apply `.github/agent-rules/requirement-input-handling.md`.

## Workflow

1. Identify the process boundary, stated trigger, and stated completion point.
2. Extract participants and their responsibilities.
3. Order supported activities and decision points.
4. Identify inputs, outputs, handoffs, exceptions, and dependencies.
5. Report missing, contradictory, or unclear process information as observations. Do not pause for clarification or invoke `custom-ba-grilling`.
6. Add a Mermaid flowchart when sequence, branching, handoffs, or three or more related steps are materially clearer as a diagram.
7. Ensure every diagram node and connection is supported by the supplied material.
8. End with a concise current-state summary.

## Output

1. `Result`
2. `Sources Used`
3. `Process Scope`
4. `Participants`
5. `Inputs and Outputs`
6. `Current-State Flow`
7. `Decision Points and Exceptions`
8. `Process Diagram` when useful
9. `Observed Gaps and Ambiguities`
10. `Summary`

## Constraints

- Describe only the current state.
- Do not propose or infer a target process unless the user separately requests one.
- Do not invent missing activities, transitions, owners, or decisions.
- Do not modify source documents.
