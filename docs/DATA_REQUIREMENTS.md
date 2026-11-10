# Data Requirements

The public repository does not include source project data.

To execute the framework with your own authorized data, the following categories are required.

## Primavera P6

Typical activity fields:
- Activity ID
- Activity Name
- Status
- Baseline Start / Finish
- Actual Start / Finish
- Remaining Duration
- Physical % Complete
- Total Float / Free Float
- WBS
- Calendar ID

Typical resource assignment fields:
- Activity ID
- Resource ID
- Planned / Remaining / Actual units
- Rate or internal unit cost
- Resource unit / type

For network reconstruction:
- P6 XER `TASK`
- `TASKPRED`
- `CALENDAR`

## Cost / Resource source

A cost-resource export such as an authorized S10 extract may provide:
- Resource ID
- Resource description
- Unit
- Unit price / internal cost
- Activity or cost-code mapping

## Optional BIM mapping

For 3D communication, use an authorized model or a synthetic/demo model with:
- Element GUID
- Work package / activity mapping
- Optional segment / location attributes

## Confidentiality

Do not commit source IFC/XER/PBIX/Excel files from a live project unless you have explicit authorization to publish them.
