# Lab 02 submission

- [Completed worksheet and report](Lab02_Completed_Worksheet_and_Report.docx) contains the prediction, sensorimotor diagram, results, and limitations. The report section starts at “รายงานสรุปผลการทดลอง Lab 02”.
- [Student controller](student_controller.py) and [recorded grader output](results/my_grade.json).
- [C0–C3 comparison](results/student_comparison), [C1 robustness](results/student_c1_short), and [C2 robustness](results/student_c2_short) contain the original student-mode configs, raw trials, and summary tables.
- Representative plots: [C1](results/student_comparison/C1_trial1.png), [C2](results/student_comparison/C2_trial1.png), and [C2 with 300 ms delay](results/student_c2_short/C2_delay300_trial1.png).

From this directory, use Python 3.10+ and choose fresh output paths.

```powershell
python -m pip install -r requirements.txt
python -m unittest discover -s tests -v
python grade_submission.py --student-file student_controller.py --out results/repro_grade.json
python lab02.py --controller-source student --protocol controller-comparison --out results/repro_comparison
python lab02.py --controller-source student --protocol robustness-short --condition C1 --out results/repro_c1
python lab02.py --controller-source student --protocol robustness-short --condition C2 --out results/repro_c2
```

The course repository is publicly accessible. For current run instructions, use the [course README](README.md) and the commands above. Recorded configurations identify the student controller by its filename relative to the lab directory and preserve its original SHA-256.

The two negative starter integration tests in this checkout point to an exact copy of the upstream starter in `tests/fixtures/student_controller_starter.py`. Their assertions are unchanged. The remaining tests and course grader retain their upstream source.
