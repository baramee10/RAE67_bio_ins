# Bio-Inspired Robotics — Lab 05

## Hormone → SO(2) CPG → Kinematic Walking

This repository contains the completed Lab 05 worksheet, experimental
report, simulation evidence, and reproducibility instructions.

## Objective

Study how the Artificial Hormone Mechanism (AHM) affects
SO(2) Central Pattern Generator (CPG) commands and simulated
hexapod kinematic locomotion.

Four conditions were compared:

- B0: Fixed controller
- B1: Direct stimulus response
- B2: Hormone-based response
- B3: Hormone binding ablation

## Environment

- Windows PowerShell
- Python 3.14.6 (requires Python 3.10+)
- No additional Python packages required

## Experiment Protocol

- Duration: 30 seconds
- Time step: 0.05 seconds
- CPG warmup: 10 seconds
- Stimulus: OFF (0–10 s), ON (10–20 s), OFF (20–30 s)

## Key Findings

- B1 maximum phi change per step: 0.200 rad
- B2 maximum phi change per step: 0.008 rad
- B2 reduced maximum command step by 96% compared with B1
- B1 command latency: 0.00 s
- B2 command latency: 0.15 s
- Total phi variation remained approximately equal

Additional experiments investigated:
- Phi-only mapping
- Invalid-input fault fallback
- Six synthetic contact signal cases

## Repository Files

- Lab05_Report.pdf — final report with figures
- Lab05_Report.docx — editable report
- Lab05_Student_Worksheet_Completed.docx — completed worksheet
- Lab05_evidence.zip — raw experimental data and source snapshots
- Lab05_RUN_COMMANDS.txt — original experiment commands

## Reproducibility

Original course code:
https://github.com/potiwat/RAE67_bio_ins

Run the commands in [Lab05_RUN_COMMANDS.txt](Lab05_RUN_COMMANDS.txt) from this lab directory. The original configurations, raw files, metrics, source snapshots and SHA-256 manifests are in [Lab05_evidence.zip](Lab05_evidence.zip).

Use fresh output directory names to avoid overwriting
previous experimental results.

## Limitations

All experimental results come from the proposed course
simulation model. They do not establish physical robot
stability, motor safety, or real-world locomotion performance.

## Reference

Ngamkajornwiwat et al. (2020).
Bio-Inspired Adaptive Locomotion Control System for Online
Adaptation of a Walking Robot on Complex Terrains.
IEEE Access. https://doi.org/10.1109/ACCESS.2020.2992794
