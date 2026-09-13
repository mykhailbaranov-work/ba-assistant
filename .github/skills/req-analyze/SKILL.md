---
name: req-analyze
description: "Analyze or summarize supplied requirements as written. Use for explanation and functional analysis, not for review, correction, rewriting, or clarification interviews."
---

# Requirements Analysis

## Purpose

Describe what the supplied requirements define: functional areas, actors, triggers, inputs, actions, outputs, conditions, and exceptions. Analyze the material as it is, without requesting extra information.

## Inputs

Apply `.github/agent-rules/requirement-input-handling.md`. Analyze only supplied requirement text and supporting evidence. Treat unavailable linked requirements as unresolved references.

## Workflow

1. Identify the supplied requirement set and context.
2. Read all available requirement text and supporting material.
3. Group requirements by functional area or business capability.
4. Extract explicitly stated actors, triggers, inputs, actions, outputs, conditions, and exceptions.
5. Trace each material point to a requirement identifier or source location.
6. Report gaps, contradictions, duplication, and unresolved references as observations.
7. End with a concise summary of the functionality described.

## Output

1. `Result`
2. `Sources Used`
3. `Functionality Overview`
4. `Key Points by Area`
5. `Traceability`
6. `Unresolved References`
7. `Observed Gaps and Ambiguities`
8. `Summary`

## Constraints

- Do not invoke `custom-ba-grilling` or pause for missing information.
- Do not review wording, propose corrections, or rewrite requirements.
- Do not infer unstated functionality or missing referenced content.
- Do not modify source documents.
