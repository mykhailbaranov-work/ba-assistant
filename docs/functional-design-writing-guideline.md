# Functional Design Document Writing Guideline

## Purpose

Define the minimum structure and evidence rules for a BA-level Functional Design Document created by the `write-functional-design` skill.

## Input Policy

Treat supplied requirements as correct. Do not review or rewrite them. Use only supplied requirements, supporting evidence, and confirmed decisions. Missing content must remain visible and must not delay creation of the supported portion of the document.

## Design Boundary

Describe the functional behavior visible to users, business roles, and interacting systems. Do not create technical architecture, internal components, API contracts, protocols, physical data models, deployment design, or implementation decisions. When such technical information is supplied, preserve it as source evidence or a stated constraint without extending it.

Technical Functional Design is outside the current workflow and may be introduced later as a separate skill.

## Structure

Use the following sections when the supplied material supports them:

1. **Document Information** — title, date, version, and sources.
2. **Purpose and Functional Overview** — supported purpose and concise description of the required behavior.
3. **Scope** — separately stated in-scope and out-of-scope boundaries.
4. **Actors and Systems** — supplied users, roles, external parties, and interacting systems.
5. **Functional Decomposition** — supported grouping of the behavior into functional areas or capabilities.
6. **Functional Flows** — ordered interactions, decisions, alternate paths, and outcomes supported by the source.
7. **Functional Requirements** — identifiable and traceable required system behavior.
8. **Business Rules** — supplied conditions, calculations, policies, and decision rules.
9. **Data Requirements** — required business data, attributes, states, and lifecycle information without inventing a physical data model.
10. **Interfaces and Integrations** — supported interactions with external systems without designing unsupported API contracts or protocols.
11. **Validations** — supplied input, state, and business validations.
12. **Exceptions and Error Handling** — supplied failure conditions, alternate outcomes, and required user-visible handling.
13. **Permissions and Access** — supplied roles, access conditions, and functional authorization behavior.
14. **Constraints and Dependencies** — supplied limitations and dependencies.
15. **Traceability** — mapping from functional content to source requirements or evidence locations.
16. **Missing Information** — unsupported information needed for a more complete FDD.

Do not create unsupported content merely to fill a section. Omit an empty optional section when omission does not hide a material gap; otherwise list the gap under `Missing Information`.

## Functional Flow Diagrams

Add a Mermaid flowchart only when actors, steps, decisions, and outcomes are supported by the source. Keep labels in English and preserve supplied terminology. Do not add inferred branches, exception paths, system interactions, or target-state behavior.

## Requirement Presentation

- Preserve requirement identifiers and meaning.
- Use consistent supplied terminology.
- Keep requirements separate from assumptions, recommendations, constraints, and implementation ideas.
- Do not convert implementation suggestions into functional requirements.
- Show source conflicts without resolving them silently.

## File Output

Use `.github/skills/write-functional-design/assets/functional-design-template.md` for content structure and the `document-output` skill for file creation. Save the result under `results/prepared_functional_design_docs/` as DOCX when a capable document MCP is available, otherwise as Markdown. Preserve the selected `source/` file's relative parent directory as defined in `.github/agent-rules/source-selection.md`.
