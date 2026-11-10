# Architecture

## 1. Schedule control
P6 snapshots are normalized into an Activity × Cut fact table. Baseline dates, current dates, remaining duration, float and physical progress are retained for traceability.

## 2. EVM and forecast
Budget/resource information is joined to activity progress to reconstruct PV, EV, AC and schedule/cost indicators. Forecast logic is kept separate from visualization.

## 3. CPM network
XER relationships are parsed into a directed schedule network. Relationship type and lag are preserved so recovery scenarios can be recalculated through the network rather than by subtracting days directly from the project finish.

## 4. Recovery candidates
Activities are prioritized using schedule exposure, remaining duration and recovery readiness.

## 5. Resource-based recovery
Only resources considered accelerable are subjected to recovery premiums. Fixed-quantity materials remain outside the crash premium unless the user explicitly changes the assumption.

## 6. Scenario engine
Four candidate activities × three recovery levels produce 3^4 = 81 combinations. Every combination is passed back through the CPM engine.

## 7. Pareto and NSGA-II
The exact frontier is calculated from the full scenario space. NSGA-II is then evaluated against that frontier as a validation exercise.

## 8. Decision layer
Power BI receives curated dimension/fact tables. BIM/3D visualization communicates current status and the spatial location/intensity of the selected recovery strategy.
