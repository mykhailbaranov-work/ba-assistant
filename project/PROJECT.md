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
