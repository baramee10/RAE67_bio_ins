# Lab 06 checker demonstration

This controlled demonstration was newly reproduced during the submission audit. The available repository history, experiment files and local checker logs yielded no record of a historical failing development run.

The temporary variant differs from the submitted policy in one transition. Inside the `event == "touch"` branch, replace `return "happy"` with `return None if current_state == "normal" else "happy"`. The `afraid` guard still applies before this branch. Use the original course checker for both runs.

| Policy | Exit code | Result |
|---|---:|---|
| Temporary variant | 1 | 39/40. `normal + touch` returned `None` and failed the baseline contract. |
| Submitted policy | 0 | 40/40. The same transition returns `"happy"`. |

Observed checker output for the variant:

```text
Checked 40 transition pairs; contract=baseline; failures=1
  normal + touch: returned None; transition does not satisfy the baseline worksheet contract
FAIL: complete TODOs in student_policy.py, then check again
```

Run from `lab_06` to reproduce the demonstration. The temporary directory is removed when the process ends.

```python
from pathlib import Path
from tempfile import TemporaryDirectory
import subprocess
import sys

policy = Path("student_policy.py")
source = policy.read_bytes()
original = b'        return "happy"'
assert source.count(original) == 1

with TemporaryDirectory() as directory:
    variant = Path(directory) / "policy_missing_normal_touch.py"
    variant.write_bytes(
        source.replace(original, b'        return None if current_state == "normal" else "happy"')
    )
    checker = [sys.executable, "-B", "check_submission.py", "--contract", "baseline"]
    assert subprocess.run([*checker, "--policy-file", str(variant)]).returncode == 1
    subprocess.run([*checker, "--policy-file", str(policy)], check=True)
```
