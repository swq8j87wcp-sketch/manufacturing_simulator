# Manufacturing Process Intelligence Simulator
**ISO 13485–Aligned SPC, FMEA, and CAPA Workflow for Yield Stability Analysis**

## Overview
This project implements a simulated manufacturing cell designed to study how hidden process disturbances impact yield, quality stability, and corrective action workflows in regulated manufacturing environments (biomedical, semiconductor, and high-reliability automation).

Rather than focusing on robot motion or control, the system models how manufacturing decisions are monitored, diagnosed, and corrected through statistical process control (SPC), failure mode and effects analysis (FMEA), and ISO-style deviation-to-CAPA pipelines.

## Dashboard Preview (Disturbance Scenario)

Below is a snapshot of the quality intelligence outputs under injected failure conditions,
showing yield degradation, defect distribution, and SPC-based process stability analysis.

![Yield Over Time](dashboard/process_log_disturbance_20260201_002704/yield_over_time.png)
![Error Heatmap](dashboard/process_log_disturbance_20260201_002704/error_heatmap.png)
![C-Chart](dashboard/process_log_disturbance_20260201_002704/c_chart.png)

## System Architecture
**Manufacturing Flow**
PICK → PLACE → INSPECT → ACCEPT / REJECT

**Quality Intelligence Layer**
- SPC Engine (C-Chart, Yield Trends)
- FMEA Auto-Generator (RPN-based prioritization)
- Deviation Detection (Rolling reject thresholds)
- CAPA Report Generator (Root Cause + Corrective / Preventive Actions)

## Experimental Design
Three controlled scenarios are executed automatically:

| Scenario     | Purpose |
|--------------|----------|
| Baseline     | Stable process, reference yield & SPC behavior |
| Disturbance | Injected failure modes to trigger deviations & CAPA |
| Recovery     | Corrective actions applied to validate yield recovery |

Each scenario produces independent logs, dashboards, and quality system outputs.

## Results Summary
| Scenario     | Yield |
|--------------|--------|
| Baseline     | ~83% |
| Disturbance | ~55% |
| Recovery     | ~83% |

Disturbance conditions reliably triggered deviation detection and automated CAPA workflows, demonstrating closed-loop manufacturing quality intelligence rather than static reporting.

## Key Features
- **Stochastic Manufacturing Simulator**  
  State-machine–based cell with probabilistic failures and configurable cycle delays.
- **SPC Dashboard**  
  Yield trends and C-Charts for special-cause variation detection.
- **Automated FMEA**  
  Risk prioritization via RPN scoring from observed defect patterns.
- **Deviation-to-CAPA Pipeline**  
  Rolling reject window triggers structured root cause analysis and corrective/preventive action templates.

## Folder Structure
data/ → Raw process logs (per scenario)
dashboard/ → SPC charts, heatmaps, FMEA tables
reports/ → ISO-style CAPA reports (Markdown/PDF)
src/ → Simulation, analysis, and reporting code

## How to Run
```bash
# Run all scenarios
python src/run_experiments.py

# Analyze a specific scenario
python src/analysis.py data/process_log_disturbance_YYYYMMDD_HHMMSS.csv

# Generate CAPA report (after copying target log to data/process_log.csv)
python src/capa_report.py
Engineering Focus

This project emphasizes:

Process stability over mechanical control

Traceability and deviation management

Data-driven corrective action systems

Quality intelligence in regulated manufacturing domains

Tech Stack

Python

Pandas / Matplotlib / Seaborn

Streamlined CSV logging

Markdown/PDF report generation

GitHub-based reproducibility
