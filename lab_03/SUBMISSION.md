# Lab 03 submission

- [Completed worksheet](worksheet.md) and [report](Lab03_SO2_CPG_Report.docx).
- [Student CPG](student_cpg.py) and [recorded grader output](results/my_grade.json).
- [Gait comparison](results/gait_comparison) contains the summary, traces, and baseline, fast, and high-gain plots.
- [Week 4 handoff](results/week4_bridge) contains the bridge trace and contract used by Lab 04.

From this directory, use Python 3.10+ and choose fresh output paths.

```powershell
python grade_submission.py --student-file student_cpg.py --out results/repro_grade.json
python cpg_walk_sim.py --condition all --output-dir results/repro_gait
python week4_bridge.py --output-dir results/repro_bridge
```

The grader exercises the student implementation. The course gait and bridge scripts produce the kinematic teaching-model evidence.
