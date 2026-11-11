# Lab 07 - Missing Response Analysis

## C1 Seed 41: clear_02
- Published messages associated with input: 100
- Accepted: 50; out-of-order: 47; dropped: 3
- Recognized events: 0
- At 9.02 s: button-channel fault, afraid -> normal
- At 9.04 s: another button fault tick
- Interpretation: Fault recovery reset the sensor filter,
  consistent with the missing clear event.
- Both latency: N/A

## C1 Seed 42: button_02
- Published messages associated with input: 11
- Accepted: 6; out-of-order: 5; dropped: 0
- Recognized events: 0
- Touch-channel fault ticks: 18.12, 18.18, 18.20 s
- Fault and idle events interrupted normal state progression.
- Interpretation: Fault resets during button activity likely
  interfered with uninterrupted debounce recognition.
- Both latency: N/A

## Conclusion
Both inputs had accepted transport messages but no
recognized event. The missing responses cannot be
attributed to packet loss alone.

These are offline simulation observations, not
physical ROS2 or hardware measurements.

Evidence:
results/completed_01/C1_r01/input_trace.csv
results/completed_01/C1_r01/events.csv
results/completed_01/C1_r01/command_trace.csv
results/completed_01/C1_r02/input_trace.csv
results/completed_01/C1_r02/events.csv
results/completed_01/C1_r02/command_trace.csv
