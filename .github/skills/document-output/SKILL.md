---
name: document-output
description: "Create an approved BA result as DOCX through an available document-generation MCP, or as Markdown when DOCX tooling is unavailable. Use only when a parent BA skill requests a file."
user-invocable: false
---

# BA Document Output

## Purpose

Render content completed by another BA skill without changing its meaning. This is a supporting skill, not a content-authoring workflow.

## Mandatory Source

Read and apply `.github/agent-rules/document-output.md`.

## Inputs

Require:

- completed document content;
- output kind: `requirements-review`, `functional-design-document`, or `prepared-requirements`;
- subject used for naming;
- applicable content template;
- confirmation state from the parent workflow.
- selected source path when the primary evidence is below `source/`.

## Workflow

1. Confirm that the parent workflow authorized file creation. `write-functional-design` and source-based `req-write` authorize automatic creation; `req-review` requires explicit user confirmation after the chat result. Chat- or attachment-based `req-write` requires the user to request a file.
2. Apply the supplied template without adding facts or changing approved wording.
3. If an available document-generation MCP can create DOCX, use it.
4. Otherwise create an equivalent Markdown file using the standard file-editing tool.
5. Save the result using the location, source-relative mapping, and naming convention defined in `.github/agent-rules/document-output.md` and `.github/agent-rules/source-selection.md`.
6. Verify that the file exists and report its format and exact repository-relative path.

## Constraints

- Do not install dependencies or create a document-generation script.
- Do not overwrite an existing file silently.
- Do not create a review report before the user confirms.
- Do not add, omit, reinterpret, or correct content supplied by the parent workflow.
- Do not delete or clean existing results automatically.
