---
name: req-review
description: "Interactively review supplied requirements for syntax, clarity, completeness, consistency, verifiability, and traceability. Use for review, validation, finding problems, or reviewing and improving requirements."
---

# Interactive Requirements Review

## Purpose

Find requirement problems, obtain a user decision for every finding, and provide traceable proposed corrections. Do not route this workflow through `custom-ba-grilling`.

## Mandatory Sources

Before reviewing, read and apply:

- `docs/requirements-writing-guideline.md`
- `.github/agent-rules/requirement-input-handling.md`
- `.github/agent-rules/source-selection.md`

If the writing reference is unavailable, report the limitation and do not claim completion.

## Review Scope

Check syntax, grammar, clarity, atomicity, completeness, consistency, traceability, verifiability, acceptance criteria, dependencies, contradictions, undefined terminology, vague qualifiers, scope, assumptions, and testability where supported by evidence.

## Interactive Workflow

1. Identify and preserve every supplied requirement and its original text.
2. Evaluate the complete requirement set and collect all findings, including syntactic errors.
3. For each finding, ask a separate question and wait for the user's answer before moving to the next finding.
4. Present this context with every question:
   - requirement identifier or source location;
   - complete original requirement text;
   - problem type;
   - explanation;
   - preliminary proposed revision.
5. Offer these responses:
   - `Not a problem (skip)`
   - `Confirm problem`
   - a free-text answer
6. Record the answer in the working `Decision Log`.
7. Interpret responses as follows:
   - `Not a problem (skip)`: preserve the finding and user answer in the final report; label the preliminary correction `Rejected proposed revision`.
   - `Confirm problem`: preserve the finding and present the checked proposed correction.
   - Free text: use the answer when producing the proposed correction. Do not run another assessment or require reconfirmation.
8. Before presenting any accepted or free-text-informed correction, check it against every applicable rule in `docs/requirements-writing-guideline.md`.
9. Produce the final review only after every finding has a recorded user answer.
10. Include only requirements for which at least one finding was detected. Omit requirements with no findings.
11. After presenting the result in chat, offer to create a review report file. Create it only if the user confirms, using `document-output` and `.github/skills/req-review/assets/review-report-template.md`. If the source is below `source/`, preserve its relative parent directory under `results/review_results_docs/`.

## Final Output

1. `Result`
2. `Sources Used`
3. `Requirements with Findings`
4. `Risks and Contradictions`
5. `Decision Log`
6. `Report File Offer`

For each finding include:

- original requirement identifier and complete text;
- problem type and explanation;
- user response;
- decision status;
- proposed correction, or the original proposal marked `Rejected proposed revision`.

Show accepted and free-text-informed revisions as a full-text diff:

```diff
- <complete original requirement>
+ <complete proposed requirement>
```

## Constraints

- Do not invoke `req-write` or `custom-ba-grilling`.
- Do not silently discard rejected findings or user answers.
- Do not include clean requirements in the final result.
- Do not present unchecked revisions or change intended business meaning.
- Do not modify source documents.
