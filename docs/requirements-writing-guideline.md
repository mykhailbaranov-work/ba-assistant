# Requirements Writing Guideline

## Purpose and Scope

The purpose of this document is to ensure consistency across products regarding how to write requirements so that all products provide a similar look and feel in the Software Development Tool.

Requirements should be clear and concise and should not leave room for personal interpretation.

## Associated Documents and Forms

- `7.0_REQ_REF01-Requirements Writing Reference`

## Procedure

### Components of a Requirement

| Component | Standard | Description |
|---|---|---|
| Subject | A requirement must form a complete sentence including a subject and predicate. The subject of the requirement is the system under discussion. If describing a specific function within the system, the function name may be included in the subject. | Example: "The cancel key shall close the option, returning the user to the main menu." |
| Predicate | The predicate is an action phrase describing the behavior the system provides. | Example: "The system shall provide the user the ability to exit the system." |
| Tense | Requirements are written in the present tense, beginning with "The system shall" when applicable. | Use the present-tense form to state mandatory system behavior. |
| Measurable result | When applicable, a requirement contains success criteria or another measurable indication of quality. | Example: "The system shall provide the ability to display a progress bar when a request to open a document has exceeded five seconds." |

### Characteristics of a Well-Written Requirement

A well-written requirement should be:

- **Correct:** Technically possible.
- **Complete:** Expresses a whole idea or statement.
- **Clear:** Unambiguous and not confusing.
- **Consistent:** Does not conflict with other requirements.
- **Testable:** Can be tested and assigned a pass or fail status.
- **Traceable:** Uniquely identified and traceable to the originating request, related test cases, and, when applicable, use cases.
- **Feasible:** Can be accomplished within the schedule.
- **Modular:** Can be changed without excessive impact.
- **Design independent:** Does not prescribe a specific solution, such as a font style or specific window size.
- **Measurable:** Provides values needed for quality and performance requirements so that adequate testing can be developed for end users.
- **Comprehensive:** Takes into account all relevant inputs and outputs. For one-to-one information mapping, define all pertinent data from the fields that must be displayed or printed. If the data must be available in the database for reports or SQL creation, define that need in the requirement.
- **Boundary values defined:** Defines software limits in boundary requirements.
- **System use:** Takes into account how the end user uses the software.

### Requirement Problems to Avoid

- **Ambiguity:** Write as clearly and explicitly as possible.
- **Multiple requirements:** Requirements containing conjunctions such as "and", "or", "with", or "also" often conflict. Their individual parts may apply separately in different situations. Split them when they express separate behaviors.
- **Negative requirements:** Avoid stating that "the system shall not" do something. Create a positive requirement stating that "the system shall prevent" the prohibited behavior.
- **Rambling:** Long, rambling sentences can lead to omissions and duplications.
- **Speculation:** Avoid generalizations or speculative words such as "usually", "generally", "often", "normally", and "typically".
- **Vague terms:** Avoid informal and unverifiable terms such as "user-friendly", "flexible", "approximately", "as possible", and "nearly". These terms do not provide a definite test for the stated property.
- **Suggestions or possibilities:** Avoid terms such as "may", "might", "should", "ought", "could", "perhaps", and "probably" when stating mandatory requirements.
- **Unachievable goals:** Avoid claims such as "100% reliable", "totally safe", "handles all unexpected failures", "pleases all users", "runs on all platforms", "never fails", and "fully compatible to all future situations".
- **Acronyms:** Avoid acronyms that can cause confusion or misunderstanding.
- **Requirement numbers:** Avoid using a requirement number within the requirement. For example, instead of writing "The system shall display error message NFR XXX if help desk is not available", write out and describe the error message within the requirement.

## Requirement Examples

### Separate Multiple Ideas

**Inappropriate:**

> The system shall be able to delete a patient's stay record and insurance information.

**Problem:** Two separate ideas are included in one requirement.

**Corrected:**

> The system shall be able to delete a patient's stay record.
>
> The system shall be able to delete a patient's insurance information.

### Describe System Behavior, Not User Capability

**Inappropriate:**

> The user shall be able to search by partial MRN number.

**Problem:** The requirement begins with "The user". Requirements describe what the system can do, not what the user can do.

**Corrected:**

> The system shall provide the ability to search by partial MRN number.

### Avoid Rambling Format

**Inappropriate:**

> The system is being enhanced when performing Order Entry searches. If a user initiates a search using only the "Ord by" field, the system displays the warning message "Ordered Date is required when searching by 'Ord by' field."

**Problem:** Incorrect format and rambling structure.

**Corrected:**

> The system shall display the warning message "Ordered Date is required when searching by 'Ord by' field" when a search is initiated using only the "Ord by" field.

### Replace Vague Terms with Defined Scope

**Inappropriate:**

> The system shall provide a method to control the editing of virtually every field.

**Problem:** The word "virtually" is not specific.

**Corrected:**

> The system shall provide a method to control the editing of all fields except the following: (followed by a list of fields affected by this requirement).

### Use Positive, Non-Acronym Wording

**Inappropriate:**

> The system shall not allow user to enter Death DT that is earlier than Birth date.

**Problems:** Use of an acronym and a negative requirement.

**Corrected:**

> The system shall prevent entering the patient's death date when it is earlier than the birth date.

### Avoid Optional Wording and Undefined Time

**Inappropriate:**

> The user should be automatically logged off if system is not used during some time.

**Problems:** The requirement begins with "The user"; "should" implies an optional behavior; and "some" is not specific.

**Corrected:**

> The system shall automatically log the user off the system after the user's time-out period has passed.

### Split Conditional Behaviors

**Inappropriate:**

> If fields are site dependent, they should display in the Read Only mode. If the fields are not site dependent, they should display in the Add/Edit mode.

**Problems:** "Should" implies an optional behavior; incorrect format; and two separate ideas are included in one requirement.

**Corrected:**

> The system shall display site dependent fields in read-only mode.
>
> The system shall display site independent fields in Add/Edit mode.

### Define Fields for Testability and Completeness

**Inappropriate:**

> The system shall display the Specimen Status Report with the applicable fields in the Header.

**Problems:** The requirement is not testable because the fields to verify are not identified. It is not comprehensive because it does not identify which input data must display on the report.

**Corrected:**

> The system shall display the following fields in the Header of the Specimen Status Report:
>
> - Name of Report
> - Clinic Logo
> - Clinic Name
> - Clinic Address
> - Ordering Location ID and Name
> - Draw Location ID and Name
> - Specimen Status
> - To Be Collected Date
> - Collected On

### Define Database Data for Its Intended Use

**Inappropriate:**

> The system shall make all data fields available in the database.

**Problem:** The requirement is not comprehensive because it does not identify which input fields must be accessible in the database or the purpose for that access.

**Corrected:**

> The system shall provide the data from the following fields for access in the creation of reports:
>
> - Clinic Name
> - Clinic Address
> - Ordering Location ID and Name
> - Draw Location ID and Name
> - Specimen Status
> - To Be Collected Date

### Define Measurable Performance

**Inappropriate:**

> The system shall maximize the performance of the system when reading the system parameters.

**Problems:** The requirement is not measurable because "maximize performance" is undefined. It is not comprehensive because it does not identify which system parameters are read or by which application or system.

**Corrected:**

> The SoftLab Order Entry Server shall apply all changes made to order entry system parameters within 10 seconds of reading them.

