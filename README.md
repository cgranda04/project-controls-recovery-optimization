# Project Controls Recovery Optimization

Portfolio demonstration of a decision-support pipeline for schedule recovery in construction / infrastructure projects.

## Why this repository exists

Traditional project controls can identify variance, but the management question is usually more operational:

> **If the project needs to recover time, where should capacity be increased, how much time can be recovered, and what is the incremental cost?**

This repository shows a reproducible architecture that connects schedule data, resource/cost information, CPM logic, recovery scenarios, multi-objective optimization and BI/BIM communication.

## Architecture

```text
Primavera P6
    ↓
Snapshots / Baseline / Logic / Resources
    ↓
EVM + Forecast + Critical Path
    ↓
Recovery Candidate Activities
    ↓
Resource-Based Recovery Cost Model
    ↓
NORMAL / MODERATE / AGGRESSIVE options
    ↓
Exhaustive Scenario Engine (3^4 = 81)
    ↓
Exact Pareto Frontier
    ↕
NSGA-II Validation
    ↓
Power BI Decision Layer
    ↓
BIM / 3D Recovery Communication
```

## What the notebook demonstrates

- Ingestion and normalization of Primavera P6 exports.
- Traceability by Activity ID and Resource ID.
- EVM and schedule forecast reconstruction.
- CPM network reconstruction from XER logic.
- Critical-path / schedule-driver analysis.
- Recovery candidate selection.
- Separation of accelerable and non-accelerable resource cost.
- Non-linear productivity assumptions for added capacity.
- Exhaustive evaluation of recovery alternatives.
- Cost-time Pareto frontier.
- NSGA-II implementation and validation against the exact solution space.
- Export of a Power BI-ready data mart.

## Recovery logic

For each selected recovery activity, three intervention levels are evaluated:

- `NORMAL`
- `MODERATE`
- `AGGRESSIVE`

Added capacity is not assumed to produce proportional productivity improvement. Each scenario therefore changes remaining duration through an explicit efficiency assumption and recalculates the CPM network before project-level recovery is measured.

The optimization problem has two competing objectives:

1. **Maximize project days recovered**
2. **Minimize incremental recovery cost**

The Pareto frontier identifies efficient alternatives. The algorithm does not replace management judgment: the final scenario should be selected using explicit project criteria and validated with Planning, Production, Cost Control and field constraints.

## Public-data policy

This repository is a **sanitized portfolio version**.

Not included:

- Original IFC model or geometry
- Real project coordinates
- Primavera P6 `.xer` files
- Original P6 Excel exports
- S10 source files
- Power BI `.pbix`
- Real resource IDs / activity descriptions
- Contractual or project-identifying documents
- Executed notebook outputs from the source project

Activity IDs, dates and labels in the public notebook are anonymized or shifted.

## Repository structure

```text
project-controls-recovery-optimization/
├── notebooks/
│   └── project_controls_recovery_public.ipynb
├── docs/
│   ├── ARCHITECTURE.md
│   └── DATA_REQUIREMENTS.md
├── data/
│   └── demo/
├── images/
├── requirements.txt
├── .gitignore
└── README.md
```

## Running with your own data

The notebook is designed as a portfolio / reusable framework. To execute it end-to-end, provide your own authorized exports using the schemas described in `docs/DATA_REQUIREMENTS.md`.

No confidential project files are required or provided in this repository.

## Tools

- Primavera P6
- Python / Google Colab
- pandas / NumPy
- NetworkX
- S10-compatible cost/resource exports
- Power BI
- BIM / Speckle as the visualization layer

## Portfolio note

This repository demonstrates methodology and software integration for Project Controls. It is not an official project record, contractual analysis or recommendation for any specific construction project.
