# Bio-Inspired Robotics — Lab 06

## Lamp Emotion and Interaction

Offline simulation of a robotic lamp emotion controller using a Finite State Machine (FSM).

This project was completed as part of the Bio-Inspired Robotics coursework.

## Objectives

- Implement a five-state FSM: normal, interested, happy, afraid, sleepy.
- Handle event priority, safety guards, timeout, and inactivity.
- Compare raw input processing (C0) against guarded processing (C1).
- Evaluate simulated motion and RGB response latency.
- Preserve experimental artifacts for verification and replay.

## Experiment Setup

| Setting | Value |
|---|---|
| Python | 3.14.6 |
| Environment | Windows PowerShell |
| Simulation duration | 22 s per run |
| Time step | 0.02 s |
| Scheduler delay | 0.04 s |
| Conditions | C0 Raw, C1 Guarded |
| Paired seeds | 41, 42, 43 |
| Repeats | 3 per condition |
| C1 debounce | 0.06 s for button/touch |

C1 additionally uses near-distance hysteresis, entering at <= 0.20 m and exiting at >= 0.28 m.

## Results

| Seed | C0 State Transitions | C1 State Transitions |
|---|---:|---:|
| 41 | 67 | 9 |
| 42 | 72 | 10 |
| 43 | 63 | 9 |
| Total | 202 | 28 |

C1 reduced the total number of state transitions by 86.14% in this simulated dataset.

Primary expected interactions with both motion and RGB onset within 1 second:
- C0: 19/21
- C1: 21/21

The guarded condition reduced unnecessary switching, but button and touch events incurred additional debounce latency.

## Run Instructions

Check the FSM transition contract:

    py -3 check_submission.py

Run three paired simulations:

    py -3 lab06.py --policy student --condition all --repeats 3 --output-dir results/new_run

Replay the recorded first input sequence:

    py -3 lab06.py --policy student --condition C1 --repeats 1 --replay results/completed_01/inputs_r01.csv --output-dir results/new_replay

Use new output directories because the runner does not overwrite nonempty result directories.

## Evidence and Documents

- student_policy.py — completed FSM transition policy
- Lab06_Report.pdf — experiment report
- Lab06_Student_Worksheet_Completed.pdf — completed worksheet
- Lab06_RUN_COMMANDS.txt — recorded run commands
- results/completed_01/ — C0/C1 experiment outputs
- results/replay_01/ — replay outputs
- Week06_Student_Worksheet_Completed.docx — editable completed worksheet

SHA-256 verification passed for all 45 files referenced by the two manifests in the committed results directories.

The original C1 Seed 41 and its replay produced byte-identical raw and event CSV files.

## Limitations

All experiments were conducted in an offline software simulation using a proposed course model. The results do not establish physical robot response time or hardware safety.

The FSM uses fixed rules and does not learn from experience.

## Course Source

Based on Lab 06 materials from:
https://github.com/potiwat/RAE67_bio_ins/tree/main/lab_06

Course-provided simulation and checker files are included to make the submission reproducible.

[Checker demonstration](CHECKER_DEMONSTRATION.md) reproduces a single failing baseline transition in a temporary policy and compares it with the submitted policy.
