# Source Registry

## Purpose

Preserve minimum technical traceability for material used in BA workflows without blocking work on unavailable administrative metadata.

## Recorded Metadata

Record when available:

- repository-relative source path;
- filename and file type;
- relevant page, sheet, section, or location;
- readability status;
- extraction limitations.

Document owner, version, purpose, confidence level, and usage restrictions are optional. Do not request them or block a workflow merely because they are absent.

## Usage Rules

- Apply `.github/agent-rules/source-selection.md` when selecting material from `source/`.
- Treat every supplied file as read-only material.
- Do not infer content from a filename or extension.
- State limitations explicitly if content is unreadable or incomplete.
- Maintain traceability from source evidence and later user decisions to resulting analysis and documents.
- Never delete or clean source or result files automatically.
