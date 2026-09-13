---
name: write-functional-design
description: "Create a BA-level Functional Design Document (FDD) from supplied, trusted requirements and save it as DOCX or Markdown. Use for functional behavior and flows, not technical architecture or API design."
---

# Functional Design Document Writing

## Purpose

Create a traceable BA-level Functional Design Document from supplied requirements and confirmed evidence. Describe required system behavior without producing technical architecture or implementation design. Treat the source requirements as correct; do not review them or run a clarification interview.

## Mandatory Sources

Read and apply:

- `docs/functional-design-writing-guideline.md`
- `.github/agent-rules/requirement-input-handling.md`
- `.github/agent-rules/source-selection.md`
- `.github/skills/write-functional-design/assets/functional-design-template.md`

## Workflow

1. Identify the feature, system, or functional area and inventory all supplied requirements and supporting evidence.
2. Confirm that the requested deliverable is BA-level functional design. If the user explicitly requests Technical Functional Design, explain that it is not currently supported and offer to create the supported BA-level document instead.
3. Map supported content to the FDD sections defined by the guideline and template.
4. Describe functional decomposition, flows, rules, data needs, integrations, validations, exceptions, and permissions only where supported by the input.
5. Add a Mermaid diagram when the supplied evidence defines a functional flow clearly enough to diagram without assumptions.
6. List absent information under `Missing Information`; do not invoke `custom-ba-grilling` or delay the supported document.
7. Preserve traceability from functional statements to their source requirements or evidence locations.
8. Use `document-output` to create the file automatically in `results/prepared_functional_design_docs/`. If the source is below `source/`, preserve its relative parent directory below that category.
9. Return a concise summary including the created format, exact path, functional scope, and missing information.

## Chat Output

1. `Summary`
2. `Created File`
3. `Functional Scope Covered`
4. `Missing Information`

## Constraints

- Do not invoke `custom-ba-grilling` or `req-review`.
- Do not invent behavior, actors, flows, rules, data, integrations, validations, exceptions, permissions, constraints, or dependencies.
- Do not design technical architecture, components, APIs, protocols, physical data models, deployment, or implementation details.
- Do not modify the supplied requirements or source documents.
- Do not return only a draft in chat; create the output file as part of the workflow.
