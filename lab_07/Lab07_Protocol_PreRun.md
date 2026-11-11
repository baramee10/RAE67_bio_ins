# Lab 07 - Pre-run Experimental Protocol

Question:
How does the modeled delay-and-drop communication profile
affect FSM responses compared with ideal delivery?

Hypothesis:
C1 may increase response latency, missing responses,
and fault ticks relative to C0.

Policy: completed_policy.py
Conditions: C0 ideal delivery; C1 combined delay and drop
Paired seeds: 41, 42, 43
Repeats: 3 per condition
Trial duration: 22 s
Time step: 0.02 s

Primary expected input IDs:
button_01, touch_01, approach_01, clear_01,
near_01, clear_02, button_02

Deadline: both motion and RGB onset within 1.0 s
Observation window: until the 22 s trial ends

Metrics:
- Published, received, dropped message counts
- State transition count
- Primary both-onset pass and missing counts
- Both-response latency
- Fault ticks

Missing response: N/A, never 0 s
Interpretation boundary:
C1 combines delay and drop, so their separate causal
effects cannot be determined from this comparison.
All timing is simulated, not physical robot timing.
