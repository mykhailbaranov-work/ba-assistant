# Release Note Writing Guideline

## 1.0 Creating Release Notes

This guideline covers Release Notes for Enhancement, Functional Design Issues.

A Release Note consists of:

- Release Note Description
- Benefit Note, required for Enhancements, Functional Design
- Implementation Note, when required

## 1.1 Release Notes for Enhancement Issues

An Enhancement Release Note must contain `Description` and `Benefit Note`. An `Implementation Note` is included when applicable.

The Description should include:

1. Identification of the enhanced functionality in the past tense, stating that it `was enhanced`. If the functionality cannot be inferred, use the applicable menu location, application entry, or location/submenu. Do not replace `was enhanced` with `has been improved`.
2. One or more past-tense sentences that clearly identify and describe the Enhancement.

### Format

> The [1] was enhanced. The [2] now provides the ability to [3].

- `[1]`: menu location or functionality name.
- `[2]`: submenu, application location, or functionality name.
- `[3]`: type of enhanced functionality.

Use the same selected release note subject for `[1]` and `[2]`. Prefer functionality names as subjects. Use menu locations or application entries only when a functionality name cannot be inferred. If multiple functionalities are identified, write exactly one Description paragraph for each functionality. If one functionality includes multiple improvements or capabilities, still write one Description paragraph for that functionality. Do not split a functionality into separate paragraphs by screen or location.

When subject clarification is needed, ask the user to choose one or more release note subjects. Each selected subject produces one Description paragraph. Suggested subjects should be functionality-based first and location-based only when functionality cannot be inferred. The user may provide custom subject values.

### Examples

> The Results Tasklist entry was enhanced. The Results Tasklist entry now provides the ability to display the Order-level User Defined Fields panel on the Tasklist Details view when the tasklist template has User Defined Fields with the `Display Separately` flag marked.

> The SoftMedia system was enhanced. The SoftMedia system now provides the ability to assign systems to a Category and group Category Setup by systems.

> The Signout Result Entry was enhanced. The Signout Result Entry now provides the ability to modify the gross section.

### 1.1.1 Benefit Note

A Benefit Note is required for all Enhancements.

The Benefit Note should:

- explain the benefit that the Enhancement brings to the software;
- use the present tense;
- identify the improvement to the system and why the functionality is useful;
- be understandable independently from the Description;
- not repeat the Description.

### Format

> The [1] enables users to [2].

- `[1]`: functionality name or summary of the change.
- `[2]`: explanation of how the Enhancement improves the workflow.

### 1.1.2 Implementation Note

An Implementation Note is applicable to Enhancement Release Notes. It is not required for every Enhancement, but it is required for CRs related to changes in Setup options or parameters.

The Implementation Note should be written in the present tense and include significant implementation information required to use the Enhancement, such as:

- Hosparam (Client Host Parameter) settings;
- security options or new security options;
- new system options;
- new database fields;
- dependencies on other modules.

If there is no implementation information, enter `N/A`.

When applicable:

- If a hosparam is added, provide its name and settings.
- If security settings or options are added, provide the name and description of the new setting.
- If a hosparam is modified or added, provide its name and all new or modified settings. Do not list existing settings that were not modified.
- If a new functionality requires specific hosparams or security options, explain the configuration in the Implementation Note.

### Format

> This functionality requires [1].

or:

> The following hosparams were added:
> - hosparam A [2]
> - hosparam B [3]

- `[1]`: required security settings, hosparam settings, or other prerequisites.
- `[2]` and `[3]`: explanation of the hosparam, setting, and system behavior based on the setting.

## 1.2 Improper Release Note Content

A Release Note should not contain:

- a reference to a TMS task;
- branch or revision information;
- `An issue has been found ...`;
- `This issue is corrected.`;
- a reference to the Client name;
- step-by-step instructions for reproducing the problem;
- references to hot fixes or fixes;
- negative terminology such as the following:
  - `Crashed`: use `The system was temporarily interrupted` or `The system experienced an abnormal termination` instead of `The system crashed and had to be rebooted`.
  - `Blown Away`: use `data loss` only when necessary, for example `The issue resulted in minor data loss`, instead of `The data was blown away`.
  - Other expressions such as `The system was taken down for three days` or `The system was locked up for hours`; use `The system was unavailable` instead.
