# Source Registry

## Source Priority

When information conflicts, use the following priority order unless a project defines a different order:

1. approved project requirements and decisions;
2. official documents from the customer and product owner;
3. internal standards and templates;
4. technical documentation;
5. external reference materials;
6. assumptions agreed upon in the current conversation.

## Local Sources

| Path | Purpose | Status |
|---|---|---|
| `docs/requirements-writing-guideline.md` | Requirements writing guideline | Requires analysis |
| `docs/release-note-writing-guideline.md` | Release note writing guideline | Requires analysis |
| `docs/use-case-writing-guideline.md` | Use case writing guideline | Requires analysis |
| `docs/functional-design-writing-guideline.md` | BA-level Functional Design Document writing guideline | Active |
| `.github/agent-rules/requirement-input-handling.md` | Requirement input and evidence boundary | Active |
| `.github/agent-rules/source-selection.md` | User source selection and result-path mapping | Active |
| `.github/agent-rules/document-output.md` | Generated document output policy | Active |

The `req-review` skill must use `docs/requirements-writing-guideline.md` for every requirements review.

The `write-release-note` skill must use the applicable issue-type section of `docs/release-note-writing-guideline.md` for every Release Note.

The `write-use-case` skill must use `docs/use-case-writing-guideline.md` for every use case.

The `write-functional-design` skill must use `docs/functional-design-writing-guideline.md` and its skill template for every BA-level Functional Design Document.

Every workflow consuming requirement text must use `.github/agent-rules/requirement-input-handling.md`.

Every workflow consuming requirements or process material must apply `.github/agent-rules/source-selection.md` when the source is not already explicit.

## Supported Input Formats

Any file type may be stored under `source/`. The project can analyze a file only when its content is available and readable in the active environment. See [`project/SUPPORTED_FILE_FORMATS.md`](SUPPORTED_FILE_FORMATS.md) for commonly readable formats and required limitations.

## Source Addition Rules

Record the repository-relative path, filename and type, relevant content location when available, readability status, and extraction limitations. Owner, version, purpose, confidence, and usage restrictions are optional and do not block work.

## Uncertainty

If a source is missing, outdated, or cannot be verified, state this explicitly. Do not replace missing information with invented data.
