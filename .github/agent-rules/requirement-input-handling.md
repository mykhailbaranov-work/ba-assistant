# Requirement Input Handling

## Purpose

Define how BA workflows identify and use requirement text supplied through files, attachments, the conversation, or the active context.

Use `.github/agent-rules/source-selection.md` first when `source/` contains user files and the source is not already explicit.

## Requirement Boundary

Separate these input classes before analysis:

- **Task instructions** tell the agent what operation to perform, what to emphasize, or how to format the result.
- **Requirement inputs** state business, user, functional, non-functional, transition, or constraint information to be analyzed or transformed.
- **Supporting evidence** provides context, business rules, examples, decisions, diagrams, or standards.

Do not review or transform task instructions as though they were requirements. If the boundary is materially unclear, ask the user to identify the requirement text before continuing.

## Source-Neutral Treatment

Apply the same evidence rules whether requirement text is:

- pasted directly into the chat;
- supplied earlier in the conversation;
- attached as a file or screenshot;
- referenced from readable repository context.

When a file below `source/` is selected, use that one file as the primary evidence. Preserve later user answers separately as confirmed decisions; do not rewrite them into the source.

Use only content that is actually available. Do not infer missing text from a filename, link, heading, or reference identifier.

## Evidence Rules

- Preserve the original requirement text and identifier when present.
- Record the source path, message, attachment, or context location supporting each material conclusion.
- Treat source documents as read-only unless the user explicitly requests their modification.
- Keep source statements separate from user decisions made during clarification or review.
- Show conflicts between sources; do not silently choose one.
- Report unreadable, incomplete, truncated, or missing content as a limitation.
- Never modify, move, replace, or delete selected source material as part of a BA workflow.
