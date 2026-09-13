# Business Analyst Work Automation

This repository defines BA Assistant, a custom agent for GitHub Copilot and Copilot CLI that supports business analysts in requirements and documentation tasks through specialized skills, instructions, and reusable templates.

## Start a Session

1. Open this repository in the GitHub Copilot app or Copilot CLI.
2. Explicitly select the `BA Assistant` custom agent (`ba-assistant` in Copilot CLI).
3. Describe the intended BA deliverable in natural language and supply the relevant requirements or source material.
4. Answer focused clarification or review questions when the selected workflow requires them.

Copilot CLI example:

```powershell
copilot --agent=ba-assistant
```

Run this command from the repository root.

The agent writes all results in English, regardless of the request language. Explicit skill invocation remains available as an optional advanced entry point.

User source files may be placed anywhere below `source/`. If that directory contains user files and the request does not already identify its source, the agent lists the files recursively and asks the user to choose `Chat and attachments` or one specific file.

## Supported Workflows

| Request | Skill |
|---|---|
| Analyze, summarize, or explain requirements | `req-analyze` |
| Review, validate, or improve requirements | `req-review` |
| Write, rewrite, or refine requirements | `req-write` |
| Create user stories | `write-user-story` |
| Analyze a current-state process | `process-analyze` |
| Write use cases | `write-use-case` |
| Write a Release Note | `write-release-note` |
| Write a BA-level Functional Design Document | `write-functional-design` |

If a request only says to "check" requirements, the agent asks whether analysis, review, or rewriting is intended. Compatible explicit requests are composed automatically.

## Important Behavior

- `req-analyze` analyzes supplied material as-is and ends with a concise summary.
- `req-review` asks for a decision on every detected finding and omits clean requirements from the final report.
- `req-write` uses `custom-ba-grilling` when material decisions are missing and performs its own quality check.
- `process-analyze` describes only the supplied current state and adds Mermaid when a diagram materially improves understanding.
- `write-functional-design` automatically creates a BA-level FDD under `results/prepared_functional_design_docs/`.
- `req-write` creates a prepared file under `results/prepared_requirements_docs/` when its primary source is below `source/`.
- After a review, the agent offers to create a report under `results/review_results_docs/`.

When a capable document-generation MCP is available, document outputs may be created as DOCX. Otherwise the agent creates Markdown without installing dependencies or adding a local DOCX generator.

## Files and Results

Place source documents in `source/`, or provide content directly in the chat or as an attachment.

Generated documents are stored by output type:

- Requirement review reports: `results/review_results_docs/`
- Functional Design Documents: `results/prepared_functional_design_docs/`
- Prepared requirements: `results/prepared_requirements_docs/`

Writing guidelines are available in `docs/`.

Source documents are treated as read-only. BA Assistant never deletes or replaces source or result files unless explicitly requested.
