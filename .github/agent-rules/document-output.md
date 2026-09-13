# Document Output

## Purpose

Define the common file-output policy for BA skills without binding the repository to a specific document service.

## Output Selection

When a skill requests a document file:

1. Use an available document-generation MCP tool capable of creating DOCX.
2. If no suitable MCP tool is available, create a Markdown file with the same approved content.
3. Do not install a package, add a generator script, or introduce a runtime dependency to create DOCX.

The parent skill controls whether file creation is automatic or requires user confirmation. File rendering must not change the approved content or add unsupported facts.

## Output Locations

- Requirements review reports: `results/review_results_docs/`
- Functional Design Documents: `results/prepared_functional_design_docs/`
- Prepared or corrected requirements: `results/prepared_requirements_docs/`

Treat these as paths relative to the repository root. Create a missing output directory only when producing an authorized output.

When the primary source is a file below `source/`, apply the relative-parent mapping defined in `.github/agent-rules/source-selection.md`. For chat and attachment sources, write directly to the applicable result category.

## Naming

Use a filesystem-safe lowercase name derived from the task, feature, entry, or functional area when available:

- `requirements-review-<subject>-<YYYY-MM-DD>.<ext>`
- `functional-design-document-<subject>-<YYYY-MM-DD>.<ext>`
- `prepared-requirements-<subject>-<YYYY-MM-DD>.<ext>`

If no meaningful subject is available, use a timestamp. Do not overwrite an existing result silently; add a timestamp or numeric suffix.

## Completion Message

Report the created format and exact repository-relative path. A Markdown fallback is a successful output and does not require a warning.

Never delete or clean generated results automatically.
