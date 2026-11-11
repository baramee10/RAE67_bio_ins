# Bio-Inspire Lab 07 — Robotic Lamp

Lab 07: ROS 2 interface design, FSM policy validation,
offline transport experiments, and an AHM-emotion proposal.

## Completed Work

- FSM policy: PASS 40/40 transition tests.
- Proposal JSON: PASS completeness checker.
- Offline simulation: C0 and C1, 3 trials each.
- Paired seeds: 41, 42, 43.
- Primary response within 1 s:
  - C0: 21/21 (100%)
  - C1: 19/21 (90.48%)
- Total emotion state transitions:
  - C0: 28
  - C1: 70
- Experiment integrity: 36 files matched SHA-256 manifest.

## Experiment Conditions

C0: Ideal simulated transport, zero delay and drop.

C1: Simulated delay (0–0.18 s), random drop (8%),
and burst drop (12.50–12.70 s).

Both conditions use the same FSM policy, input schedule,
paired seeds, and controller configuration.

These results come from a 22-second virtual-time offline
simulation, not a physical robot or real ROS 2 network.

## Validation

Run from the lab_07 directory using Python 3.10 or later:

    py -3 check_submission.py --contract group

    py -3 check_proposal.py proposal.json

To reproduce the offline experiment in a new directory:

    py -3 offline_lab.py --condition all --repeats 3 --output-dir results/reproduce_01

## Documents

- Lab07_Experimental_Proposal.docx
- Week07_Student_Worksheet_Completed.docx
- Lab07_Protocol_PreRun.md
- Lab07_Missing_Analysis.md
- proposal.json

## Limitations and Future Work

- AHM-emotion integration is proposed, not yet implemented.
- SO(2) CPG is documented as a proposed model.
- ROS 2 and micro-ROS hardware integration is not verified.
- Real robot tests and the 600-second human interaction
  scenario remain planned work.
- The original six offline trials, raw traces, configs, metrics, source snapshot and SHA-256 manifest are packaged in [Lab07_offline_evidence.zip](Lab07_offline_evidence.zip). Extract it from this directory to recover `results/completed_01/`. Fresh runner outputs remain ignored.

## Attribution

Based on teaching materials and starter code from:
https://github.com/potiwat/RAE67_bio_ins

The completed FSM policy from Lab 06 is installed at [lamp_week07/student_policy.py](lamp_week07/student_policy.py). The historical protocol called the same bytes completed_policy.py. The [course README](README.md) describes how to copy the policy into a ROS workspace when needed.

The worksheet, proposal, and proposal JSON use the same relative research schedule: Week 1 proposal and AHM/CPG preparation, Week 2 ROS 2 setup and 600-second simulation, Week 3 real-robot trials after safety verification and consent, and Week 4 evidence review and reporting. The official course deadline follows the instructor’s announcement. Confirm the instructor’s delivery channel if the archive must also be uploaded separately.
