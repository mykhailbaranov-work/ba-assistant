# Repository Working Rules

This repository defines a GitHub Copilot business-analysis agent, its skills, and supporting standards. It is not an application project and does not require an application build or runtime for ordinary work.

- Treat `README.md`, `docs/`, and `project/` as documentation, not as executable application code.
- Keep repository-wide instructions short. Business-analysis routing, output language, and workflow behavior belong to `.github/agents/ba-assistant.agent.md` and the applicable skill.
- Keep each workflow rule in one authoritative location. Do not duplicate detailed skill procedures in this file, the agent profile, prompts, or README.
- Before completing any change to agent runtime behavior, analyze dependent project instructions and artifacts. Check `.github/agents/ba-assistant.agent.md`, relevant `.github/skills/*/SKILL.md` files, `.github/agent-rules/*`, `docs/*` guidelines and templates, `project/SOURCES.md`, `project/SUPPORTED_FILE_FORMATS.md`, `README.md`, MCP availability and fallback behavior, output directories, and result-path rules as applicable.
- Changes to routing, skill composition, MCP behavior, source handling, output format, fallback behavior, prohibited behavior, or user-facing workflow must update `tests/routing-scenarios.md` or explicitly identify the existing scenario that covers the change before the work is complete.
- For agent, skill, or runtime-behavior changes, the final response must include `Dependency impact: <checked/updated items>. Scenario coverage: <added scenario(s) or existing scenario(s)>`.
- Treat supplied source documents as read-only unless the user explicitly requests a source-document modification.
- Do not modify generated or source files unless the user's request authorizes the change.
