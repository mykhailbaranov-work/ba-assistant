# Business Analyst Work Automation

## Purpose

This project defines the conversational `BA Assistant` custom agent for the GitHub Copilot app and Copilot CLI. It automates repeatable business-analysis workflows through a small routing layer and specialized skills. The repository does not contain or require an application runtime.

## Operating Model

The user explicitly selects the `BA Assistant` agent (`ba-assistant` in Copilot CLI) and requests a deliverable in natural language. The agent identifies the intended output and invokes the applicable skill. Explicit skill invocation is optional.

The selected agent writes all user-facing content and generated documents in English. This language rule belongs to the custom agent and does not apply to other agents using the repository.

## Architecture

- `.github/copilot-instructions.md` contains only repository-wide maintenance context.
- `.github/agents/ba-assistant.agent.md` owns intent routing, shared BA constraints, and output language.
- Each `.github/skills/<name>/SKILL.md` owns one workflow and its output format.
- `.github/agent-rules/` contains shared execution and evidence policies.
- `docs/` contains writing guidelines only.
- `project/` contains architecture, source-governance, and supported-format documentation.
- Skill `assets/` contain output templates.
- `source/` contains Git-ignored user inputs.
- `results/` contains Git-ignored generated deliverables grouped by output kind.
- `README.md` explains usage but is not an authoritative workflow source.

Detailed procedures must not be duplicated across these layers.

## Current Skills

### `custom-ba-grilling`

Clarifies material requirement ambiguity when explicitly invoked by another workflow and returns a Decision Log and clarification handoff.

### `req-analyze`

Analyzes supplied requirements as written, reports observations without asking for extra information, and ends with a concise summary.

### `req-review`

Reviews requirements interactively. It asks a separate decision question for every finding, records the answer, and reports only requirements for which findings were detected.

### `req-write`

Creates or refines requirements, uses `custom-ba-grilling` when decisions are materially unclear, and performs its own non-interactive quality check without invoking `req-review`.

### `write-user-story`

Creates traceable user stories and acceptance criteria from requirements treated as correct. It uses clarification only when material ambiguity prevents a supported story.

### `process-analyze`

Describes a supplied current-state process, including participants, steps, decisions, inputs, outputs, exceptions, and observed gaps. It may add a supported Mermaid flowchart.

### `write-use-case`

Invokes `req-analyze` first and writes use cases according to `docs/use-case-writing-guideline.md`.

### `write-release-note`

Writes a Release Note from the complete supplied requirements, issue type, and expanded functionality or application entry information.

### `write-functional-design`

Creates a supported BA-level Functional Design Document from requirements treated as correct and automatically saves it under `results/prepared_functional_design_docs/`.

### `document-output`

Internal supporting skill that creates DOCX through an available document-generation MCP, or Markdown when such a tool is unavailable.

## Shared Principles

1. Do not invent requirements, business rules, decisions, source content, or missing values.
2. Keep task instructions separate from requirement inputs.
3. Apply identical evidence handling to requirements supplied through chat, files, attachments, or context.
4. Keep supplied documents read-only and preserve source traceability.
5. Surface source conflicts and missing information explicitly.
6. Create generated output as a new artifact, never by overwriting a source silently.
7. Select at most one file below `source/` for a workflow and preserve its relative parent path below the result category.
8. Never delete or clean source and result files automatically.

## Source Selection

- If the request explicitly identifies a source file, requirement or process text, or an attachment, use that source without asking again.
- If `source/` contains no real user files, use chat and attachments without presenting a choice.
- Otherwise list all user files recursively and ask the user to choose `Chat and attachments` or one file.
- Ignore `.gitkeep` and other repository placeholders when determining whether `source/` contains user files.
- If several files are requested, ask the user to select one.
- If the selected file cannot be read, report the limitation and request another file or a readable export.

## Navigator MCP Server

BA Assistant users are expected to install the Navigator MCP server globally in their GitHub Copilot app accounts. The BA Assistant must not define, install, configure, or assume ownership of the Navigator MCP server, and must not add Navigator-specific MCP server configuration to the agent.

Use Navigator to find requirements when the user asks to find requirements and the requirement text is not already available in the current conversation context or selected source. Requirement IDs from context without requirement text are not sufficient source content.

When finding requirements by ID, use the complete requirement ID by default, including all prefixes and suffixes. Treat requirement IDs case-insensitively and return them in canonical uppercase form.

Normalize partial DA LIS requirement IDs as follows:

- `32212` -> `DA-LIS-FR-32212IS` and `DA-LIS-FR-32212IT`
- `32212IS` -> `DA-LIS-FR-32212IS`
- `32212IT` -> `DA-LIS-FR-32212IT`
- `FR-32212IS` -> `DA-LIS-FR-32212IS`
- `FR-32212IT` -> `DA-LIS-FR-32212IT`
- `LIS-FR-32212IS` -> `DA-LIS-FR-32212IS`
- `LIS-FR-32212IT` -> `DA-LIS-FR-32212IT`
- Full IDs such as `DA-LIS-FR-32212IS` or `DA-LIS-FR-32212IT` -> use as provided, normalized to uppercase.

If the user request contains both an ID-like value and keyword text, perform ID lookup first. If ID lookup finds a requirement, return it. If ID lookup creates both `IS` and `IT` candidates, use the keyword text only to rank or disambiguate the candidate results; do not replace ID lookup with keyword search.

Use keyword search when the user explicitly asks to find requirements by keyword, or when the user asks to find requirements for, about, or related to a phrase without providing an ID-like value.

Return requirement search results as a table with these columns:

`ID | Name | Description | Rev | Status | Created | Modified`

Use `Not available` for missing fields. Do not invent missing values.

For keyword search, return the most relevant matches first. For ID search, return exact full ID matches first, then normalized candidate matches. Return at most 30 results. If more than 30 results are available, show the top 30 and ask the user to narrow the search.

If Navigator is not available in the current Copilot session and requirement text is not available in the current conversation context or selected source, do not add Navigator configuration. State that Navigator is not available in the current Copilot session and that requirement text is not available in context/source.

## Document Outputs

- Review results are always shown in chat. A file is created under `results/review_results_docs/` only after user confirmation.
- Functional Design Documents are created automatically under `results/prepared_functional_design_docs/`.
- Prepared requirements from a selected `source/` file are created automatically under `results/prepared_requirements_docs/`.
- DOCX is preferred when a capable document-generation MCP is available.
- Markdown is the automatic fallback and is a successful result, not a warning condition.
- No local DOCX generator or third-party package is required by this repository.
- When a source file is nested, generated output mirrors its relative parent directory.

## Validation

`tests/routing-scenarios.md` defines manual scenarios for intent selection, skill composition, clarification behavior, outputs, and prohibited behavior.

## Planned Extension

Technical Functional Design may be added later as a separate workflow. It must not be treated as an alias for the current BA-level `write-functional-design` skill.

Other BA workflows may be added as narrowly scoped skills. A new skill must have a discriminating description, one authoritative procedure, explicit input boundaries, a defined output format, and routing scenarios before it is considered complete.
