# Lab 04 submission

- [Completed Markdown worksheet](worksheet.md), [completed Word worksheet](Lab04_Student_Worksheet_Completed.docx), [report](Lab04_Final_Report_TH.docx), and [block diagram](Lab04_Block_Diagram.png).
- [Student hormone controller](student_hormone.py) and [course checker](check_submission.py).
- Original evidence: [comparison](results/comparison), [zero](results/zero), [one](results/one), [spike](results/spike), [fault](results/fault), and [Week 3 handoff](results/handoff_from_lab03).

From this directory, use Python 3.10+ and the [course run commands](README.md), choosing fresh output paths. The bundled [Lab 03 handoff contract](../lab_03/results/week4_bridge/handoff_contract.json) can be used directly.

```powershell
python check_submission.py --student-file student_hormone.py
python lab04.py --controller-source student --condition all --profile step --output-dir results/repro_comparison
python lab04.py --controller-source student --condition C1 --profile zero --contract ../lab_03/results/week4_bridge/handoff_contract.json --output-dir results/repro_handoff
```
