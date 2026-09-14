# Navigator MCP

## Purpose

Find and normalize requirement records through an available Navigator MCP server without making the BA Assistant own the server configuration.

## Availability

BA Assistant users are expected to install the Navigator MCP server globally in their GitHub Copilot app accounts. The BA Assistant must not define, install, configure, or assume ownership of the Navigator MCP server, and must not add Navigator-specific MCP server configuration to the agent.

Use Navigator to find requirements when the user asks to find requirements and the requirement text is not already available in the current conversation context or selected source. Requirement IDs from context without requirement text are not sufficient source content.

If Navigator is not available in the current Copilot session and requirement text is not available in the current conversation context or selected source, do not add Navigator configuration. State that Navigator is not available in the current Copilot session and that requirement text is not available in context/source.

## Lookup Strategy

When finding requirements by ID, use the complete requirement ID by default, including all prefixes and suffixes. Treat requirement IDs case-insensitively and return them in canonical uppercase form.

Normalize partial DA LIS requirement IDs as follows:

- `32212` -> `DA-LIS-FR-32212IS` and `DA-LIS-FR-32212IT`
- `32212IS` -> `DA-LIS-FR-32212IS`
- `32212IT` -> `DA-LIS-FR-32212IT`
- `FR-32212IS` -> `DA-LIS-FR-32212IS`
- `FR-32212IT` -> `DA-LIS-FR-32212IT`
- `LIS-FR-32212IS` -> `DA-LIS-FR-32212IS`
- `LIS-FR-32212IT` -> `DA-LIS-FR-32212IT`
- Full IDs such as `DA-LIS-FR-32212IS` or `DA-LIS-FR-32212IT` -> use as provided, normalized to uppercase.

If the user request contains both an ID-like value and keyword text, perform ID lookup first. If ID lookup finds a requirement, return it. If ID lookup creates both `IS` and `IT` candidates, use the keyword text only to rank or disambiguate the candidate results; do not replace ID lookup with keyword search.

Use keyword search when the user explicitly asks to find requirements by keyword, or when the user asks to find requirements for, about, or related to a phrase without providing an ID-like value.

For keyword search, return the most relevant matches first. For ID search, return exact full ID matches first, then normalized candidate matches. Return at most 30 results. If more than 30 results are available, show the top 30 and ask the user to narrow the search.

## Result Normalization

Return requirement search results as a table with these columns:

`ID | Name | Description | Rev | Status | Created | Modified`

Navigator MCP server responses may have their own raw structure. The BA Assistant must normalize Navigator requirement results before presenting them to the user. Treat raw MCP output as any unprocessed Navigator response that has not been mapped into the BA Assistant requirement result format. Do not expose raw MCP output as the final answer unless the user explicitly asks for raw output.

When the required fields are available in the MCP response, map them to the standard output table. Use obvious semantic equivalents, such as `title` or `name` for `Name`, and `updated`, `updatedAt`, or `modifiedAt` for `Modified`. Use requirement `description`, `text`, `body`, `content`, or equivalent requirement text for `Description`, preferring an explicit description field when available.

If a field is missing or cannot be reliably derived, use `Not available`. Do not invent missing values or infer values from unrelated text, internal metadata, or naming conventions.

If Navigator returns a response that cannot be normalized reliably, state that Navigator returned a response that could not be normalized reliably. Show only reliably extracted fields and use `Not available` for the rest.

For requirement search, final output should include requirement records only. Mention non-requirement matches only when they explain why no requirement was found or when the user asked for broader Navigator results.

If the user explicitly asks for raw output, show the relevant raw Navigator output as-is.
