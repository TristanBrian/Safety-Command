Capstone Progress Check — Week 7
Team: NULL_TERMINATORS (KPC Cohort, Inuka Fellowship, Power Learn Project)
Capstone: Predictive Maintenance for KPC Pipeline Pump Infrastructure
Submitted by: Brian Kioko ML & Modelling Engineering Lead
Date: 2026-08-10

Did you start building your Capstone dashboard?

Not yet on the frontend dashboard, as we are following our Implementation Rollout Plan, currently in Phase 1 — Discovery and Data Assessment (Weeks 7–12).
However, I have already started building the data pipelines that will support the dashboard. My main focus is the Flowgard reconciliation module, which is a core component of our solution.


Current progress includes:
Developing Python scripts to align historical SCADA telemetry, including pressure, flow, and motor current, with Flowgard hydraulic simulation outputs.
Calculating performance residuals using Actual Pressure - Simulated Pressure for the 24-pump synthetic dataset.
Using these residuals as the primary Health Indicator (HI) for future dashboard risk visualizations.
Structuring time-series data using Pandas HDF5 stores to support efficient pump-level degradation analysis.

What library are you using?

The team has selected Next.js for the stakeholder-facing dashboard. My current work is focused primarily on backend and data engineering.
The main libraries being used are:
Pandas and NumPy : Data cleaning, transformation, and reconciliation calculations.
SciPy : Smoothing and filtering residual data, including EWMA-based analysis.
Scikit-learn : Feature engineering and development of risk-score inputs.
The outputs are being structured as clean CSV and JSON datasets so that the frontend can consume ready-to-visualize data without directly interacting with the raw hydraulic models.

One challenge faced or anticipated in visualizing our Capstone data

Synthetic Data vs. Real-World Operations
One of the main challenges identified is the difference between our current synthetic dataset and real KPC SCADA operating conditions.
Our current dataset contains 24 pumps across 4 depots, but it does not include operational event flags such as product changes, pump start/stop sequences, or other operational transitions.
During testing, the synthetic reconciliation residuals produced relatively linear degradation patterns. In a real operational environment, these patterns are likely to be affected by operational transients and other system events.
This creates a potential risk of false alarms if anomaly thresholds are developed solely from the clean synthetic dataset.

Proposed Solution

To address this, I am designing a two-tier data and visualization approach:
Raw Residuals View
Displays the complete residual data, including operational spikes and variations. This view will primarily support data engineers and technical users.
Degradation Trend View
Applies smoothing and filtering to the residual data to highlight longer-term degradation trends. This view will be designed for KPC operators and other stakeholders.
The filtering parameters will be documented so that the frontend team can clearly identify which dataset should be used for operational dashboards and which should be used for technical analysis.

Next Milestone

Complete the Flowgard reconciliation pipeline for all 24 synthetic pumps and deliver a clean feature store in CSV/Parquet format to Ingrid by the end of Week 8.
This will provide the structured data required for the Next.js dashboard scaffolding when the project moves into Phase 2.

Summary

Week 7 has focused primarily on building the data foundation rather than the frontend interface.
The key objective is to ensure that the dashboard is eventually powered by clean, validated, and meaningful predictive-maintenance indicators rather than raw sensor data alone.