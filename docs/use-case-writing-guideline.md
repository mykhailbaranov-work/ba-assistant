# Use Case Writing Guideline

## 1.0 Structure of a Use Case

Every use case must be documented using the following elements:

- **Name** — a clear verb/noun or actor/verb/noun descriptor that communicates the scope of the use case.
- **Brief Description** — a brief paragraph of text describing the scope of the use case.
- **Actors** — a list of the types of users who can engage in the activities described in the use case, for example `User`, `System`. A third actor is optional and can be used for integration use cases with other systems. Actor names should not correspond to job titles.
- **Preconditions** — anything the solution can assume to be true when the use case begins.
- **Basic Flow** — the main flow, documented in the Description field. It describes the steps taken by the actors to accomplish the goal of the use case, and clearly describes what the system does in response to each user action.
- **Alternative Flows** — the less common user/system interactions, documented as described in `1.1 Alternative Flows` when such flows exist. Optional if not needed.
- **Exception Flows** — the things that can happen that prevent the user from achieving their goal, such as providing an incorrect username and password, documented as described in `1.2 Exception Flows` when such flows exist. Optional if not needed.

## 1.1 Alternative Flows

- Create an alternative flow when the source requirements describe an option, configuration parameter, flag, or mode that changes system behavior by introducing a different sequence of actions, validation, external call, status, permission check, or result.
- Treat conditions expressed as enabled/disabled options, turned on/off configuration parameters, marked/unmarked flags, selected modes, or threshold-based settings as candidates for alternative flows when they change how the system behaves.
- Do not create alternative flows for simple field values, filters, sorting, labels, text options, or display preferences unless they introduce different system behavior.
- Short alternative flows (1-3 steps) can be documented either in the body of the use case or as child use cases.
- Longer alternative flows (more than 3 steps) shall be documented as child use cases.
- For each alternative flow, clearly indicate that it is an alternative flow, and assign a sequence number and a name.

### Format

> Alternative Flow [n] - [Name]

### Example

> Alternative Flow 4 - Ordering Additional Test

## 1.2 Exception Flows

- Short exception flows (1-3 steps) can be documented either in the body of the use case or as child use cases.
- Longer exception flows (more than 3 steps) shall be documented as child use cases.
- For each exception flow, clearly indicate that it is an exception flow, and assign a sequence number and a name.

### Format

> Exception Flow [n] - [Name]

### Example

> Exception Flow 4 - Wrong Test

## 1.3 Step Labels

Step labels apply only to alternative and exception flows, and to the steps a flow moves to when it says "go to". The `Basic Flow` uses standard sequential numbering (1, 2, 3, ...) and does not use step labels.

Use the following conventions when assigning labels to steps:

- `A1`, `A2`, ... — steps that are start points for alternative flows.
- `E1`, `E2`, ... — steps that are start points for exception flows.
- `G1`, `G2`, ... — "go to" steps, where a flow moves from one step to another step.

## 1.4 Improper Use Case Content

A use case should not contain:

- implementation or UI design details that are not required to understand the flow;
- job titles used as actor names;
- an alternative or exception flow longer than 3 steps documented inline instead of as a child use case;
- an alternative or exception flow without an assigned sequence number and name;
- a "go to" step without an assigned label;
- step labels (`A#`, `E#`, `G#`) used in the `Basic Flow` instead of standard numbering;
- a reference to a requirement, requirement identifier, or phrasing such as "where required by the applicable requirement" within the `Name`, `Brief Description`, `Actors`, `Preconditions`, or any flow. Requirement traceability belongs only in the dedicated list of covered requirements at the end of the use case, not inline in its text.
