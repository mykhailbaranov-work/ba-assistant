# Repository Working Rules

This repository defines a GitHub Copilot business-analysis agent, its skills, and supporting standards. It is not an application project and does not require an application build or runtime for ordinary work.

- Treat `README.md`, `docs/`, and `project/` as documentation, not as executable application code.
- Keep repository-wide instructions short. Business-analysis routing, output language, and workflow behavior belong to `.github/agents/ba-assistant.agent.md` and the applicable skill.
- Keep each workflow rule in one authoritative location. Do not duplicate detailed skill procedures in this file, the agent profile, prompts, or README.
- Treat supplied source documents as read-only unless the user explicitly requests a source-document modification.
- Do not modify generated or source files unless the user's request authorizes the change.
