# Source Selection

## Purpose

Select one authoritative input source for a BA workflow while keeping user files read-only and preventing unrelated files from entering the context.

## Preflight

Apply this preflight before a BA workflow consumes requirements or process material:

1. Inspect `source/` recursively for user files. Ignore `.gitkeep` and other repository placeholder files.
2. If the user explicitly identifies a source file, use it without asking again.
3. If the user supplies requirement or process text directly in the request, or attaches a file, treat `Chat and attachments` as explicitly selected.
4. If `source/` contains no user files, use the available chat and attachment content without presenting a source choice.
5. Otherwise list every user file under `source/` by repository-relative path and ask the user to choose either:
   - `Chat and attachments`; or
   - one specific file from the list.
6. Do not start the primary workflow until the source is selected.

## Selection Rules

- Accept one `source/` file per workflow.
- If the user selects several files or a directory, explain the one-file boundary and ask them to choose one file.
- Do not silently combine multiple files into one requirement set.
- Do not copy attachments into `source/` automatically.
- Keep the selected source file as the primary evidence. Record later user answers separately as confirmed user decisions.

## Readability

The presence or extension of a file does not guarantee that its content can be read.

If the selected file is unreadable, unsupported in the active environment, encrypted, corrupted, or only partially available:

1. state the readability status and limitation;
2. do not infer content from the filename or extension;
3. show the available source-file list again;
4. ask the user to choose another file or provide a readable export or attachment.

## Result Path Mapping

When the selected file is below `source/`, preserve its relative parent directory below the applicable result category.

Example:

```text
source/project-a/feature-1/requirements.docx
results/review_results_docs/project-a/feature-1/<review-file>
results/prepared_functional_design_docs/project-a/feature-1/<functional-design-file>
results/prepared_requirements_docs/project-a/feature-1/<requirements-file>
```

For chat or attachment sources, save a requested file directly under the applicable result category.

## Source Lifecycle

- Never modify, overwrite, move, rename, or delete a file in `source/` unless the user makes a separate explicit request for that exact operation.
- Create corrected or transformed content as a new result file.
- Never delete or clean files from `source/` or `results/` automatically.

## Minimum Metadata

Record only metadata available without blocking the workflow:

- repository-relative source path;
- filename and file type;
- relevant page, sheet, section, or location when available;
- readability status and extraction limitations.
