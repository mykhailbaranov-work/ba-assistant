# BA Assistant Routing Scenarios

These are manual behavioral checks. Run them with the `BA Assistant` agent explicitly selected (`ba-assistant` in Copilot CLI). Every response must be in English.

## Scenario 1: Analyze Requirements

- **User request:** `Analyze and summarize these requirements: <requirements>`
- **Expected primary skill:** `req-analyze`
- **Expected supporting skills:** None
- **Expected behavior:** Analyze only supplied content and end with `Summary`.
- **Prohibited behavior:** `custom-ba-grilling`, corrections, rewriting.

## Scenario 2: Ambiguous Check Request

- **User request:** `Check these requirements: <requirements>`
- **Expected primary skill:** None until clarified
- **Expected behavior:** Ask whether the user wants analysis, review, or rewriting.
- **Prohibited behavior:** Silently selecting one workflow.

## Scenario 3: Interactive Review

- **User request:** `Review and improve these requirements: <requirements containing at least two defects>`
- **Expected primary skill:** `req-review`
- **Expected supporting skills:** None before file creation
- **Expected behavior:** Ask a separate question for each finding with original text, type, explanation, preliminary revision, and the three response modes. Record every answer.
- **Prohibited behavior:** `req-write`, `custom-ba-grilling`, final review before all findings receive answers.

## Scenario 4: Rejected Review Finding

- **User response:** `Not a problem (skip)`
- **Expected primary skill:** `req-review`
- **Expected behavior:** Keep the finding and response in the final result and label the preliminary correction `Rejected proposed revision`.
- **Prohibited behavior:** Discarding the finding or presenting the rejected correction as accepted.

## Scenario 5: Review Report File

- **User request:** After review, confirm creation of the report file.
- **Expected supporting skill:** `document-output`
- **Expected behavior:** Create DOCX through an available document MCP; otherwise create Markdown under `results/review_results_docs/`. Report format and exact path.
- **Prohibited behavior:** Creating the file before confirmation or installing a DOCX dependency.

## Scenario 6: Write Requirements

- **User request:** `Write functional requirements from this incomplete feature description: <description>`
- **Expected primary skill:** `req-write`
- **Expected supporting skill:** `custom-ba-grilling`
- **Expected behavior:** Resolve material ambiguity, draft requirements, and perform an internal writing-reference quality check.
- **Prohibited behavior:** `req-review`.

## Scenario 7: Write User Stories

- **User request:** `Create user stories from these requirements: <complete requirements>`
- **Expected primary skill:** `write-user-story`
- **Expected supporting skills:** None when the requirements are unambiguous
- **Expected behavior:** Produce traceable stories and supported acceptance criteria.
- **Prohibited behavior:** Reviewing or correcting source requirements.

## Scenario 8: Analyze Current Process

- **User request:** `Analyze this current process: <multi-step process with a branch>`
- **Expected primary skill:** `process-analyze`
- **Expected behavior:** Describe only the current state and include a source-supported Mermaid flowchart.
- **Prohibited behavior:** Inventing or recommending a target process.

## Scenario 9: Write Use Case

- **User request:** `Write a use case from these requirements: <requirements>`
- **Expected primary skill:** `write-use-case`
- **Expected supporting skill:** `req-analyze`
- **Expected behavior:** Analyze first, apply the guideline, and list covered requirements separately.
- **Prohibited behavior:** Drafting directly from raw requirements or placing requirement IDs in flows.

## Scenario 10: Write Release Note with Missing Entry

- **User request:** `Write a Release Note for this Bug: <complete requirements without functionality name or location>`
- **Expected primary skill:** `write-release-note`
- **Expected behavior:** Ask a targeted question for the expanded functionality, application entry, or location/submenu.
- **Prohibited behavior:** `custom-ba-grilling` or an invented entry name.

## Scenario 11: Write BA-level Functional Design

- **User request:** `Write a Functional Design Document from these requirements: <requirements>`
- **Expected primary skill:** `write-functional-design`
- **Expected supporting skill:** `document-output`
- **Expected behavior:** Create the supported BA-level FDD automatically, include a source-supported Mermaid flowchart when possible, list missing information, and return a concise summary with format and exact path.
- **Prohibited behavior:** `custom-ba-grilling`, `req-review`, or returning only a chat draft.

## Scenario 12: Functional Design Markdown Fallback

- **Precondition:** No document-generation MCP capable of DOCX is available.
- **User request:** `Prepare an FDD from these requirements: <requirements>`
- **Expected primary skill:** `write-functional-design`
- **Expected supporting skill:** `document-output`
- **Expected behavior:** Create Markdown automatically under `results/prepared_functional_design_docs/` and report its format and exact path without a warning.
- **Prohibited behavior:** Installing dependencies, creating a generator script, or failing solely because DOCX is unavailable.

## Scenario 13: Compatible Compound Request

- **User request:** `Analyze these requirements and write a use case.`
- **Expected primary skill:** `write-use-case`
- **Expected supporting skill:** `req-analyze`
- **Expected behavior:** Execute the compatible chain automatically.
- **Prohibited behavior:** Asking the user to choose between the two requested results.

## Scenario 14: Requirement Boundary

- **User request:** `Review this requirement and focus on permissions: The system shall display all accounts.`
- **Expected primary skill:** `req-review`
- **Expected behavior:** Treat the first clause as a task instruction and the second as requirement text.
- **Prohibited behavior:** Reviewing the task instruction as a requirement.

## Scenario 15: Empty Source Directory

- **Precondition:** `source/` contains only `.gitkeep`.
- **User request:** `Analyze these requirements: <requirements>`
- **Expected behavior:** Treat chat as the explicit source and start `req-analyze` without presenting a source choice.
- **Prohibited behavior:** Listing `.gitkeep` as a user file.

## Scenario 16: Select a Source File

- **Precondition:** `source/` contains user files and the request supplies no requirement text or attachment.
- **User request:** `Review requirements.`
- **Expected behavior:** Recursively list every user file by relative path and ask the user to choose `Chat and attachments` or one specific file.
- **Prohibited behavior:** Reading all files or selecting one silently.

## Scenario 17: Explicit Source Path

- **User request:** `Review source/project-a/feature-1/requirements.docx.`
- **Expected behavior:** Use the named file without asking the user to select a source again.
- **Prohibited behavior:** Presenting a redundant source-selection question.

## Scenario 18: Multiple Source Files

- **User request:** `Analyze source/a.md and source/b.md.`
- **Expected behavior:** Explain that one source file is accepted per workflow and ask the user to select one.
- **Prohibited behavior:** Combining the files silently.

## Scenario 19: Unreadable Source File

- **Precondition:** The selected source file cannot be read in the active environment.
- **Expected behavior:** Report the readability limitation, list available source files again, and request another file or a readable export or attachment.
- **Prohibited behavior:** Inferring content from the filename or extension.

## Scenario 20: Mirrored Review Path

- **Selected source:** `source/project-a/feature-1/requirements.docx`
- **User request:** Confirm creation of the completed review report.
- **Expected behavior:** Create the result below `results/review_results_docs/project-a/feature-1/`.
- **Prohibited behavior:** Writing into `source/` or flattening the source-relative parent path.

## Scenario 21: Prepared Requirements Output

- **Selected source:** `source/project-a/feature-1/requirements.docx`
- **User request:** `Rewrite these requirements.`
- **Expected primary skill:** `req-write`
- **Expected supporting skills:** `custom-ba-grilling` when materially needed, then `document-output`
- **Expected behavior:** Keep the source unchanged and create the prepared result below `results/prepared_requirements_docs/project-a/feature-1/`.
- **Prohibited behavior:** Modifying the source or invoking `req-review`.

## Scenario 22: No Automatic Cleanup

- **Precondition:** `source/` and `results/` contain existing user files.
- **User request:** Run any ordinary BA workflow.
- **Expected behavior:** Leave all unrelated source and result files unchanged.
- **Prohibited behavior:** Deleting, replacing, moving, renaming, or cleaning files automatically.

## Scenario 23: Technical Functional Design Request

- **User request:** `Create a Technical Functional Design with API contracts and component architecture.`
- **Expected primary skill:** None until the user accepts the supported scope
- **Expected behavior:** Explain that only BA-level Functional Design Documents are currently supported and offer to create that document instead.
- **Prohibited behavior:** Routing automatically to `write-functional-design` or inventing technical design details.
