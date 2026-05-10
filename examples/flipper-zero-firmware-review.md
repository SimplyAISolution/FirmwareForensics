# Flipper Zero Firmware Review Example

## Summary

A companion firmware module behaves inconsistently during wireless scanning.

## System Context

- Device class: Flipper Zero companion or related open-source firmware module
- Symptom: wireless scan intermittently stops, misses results, or becomes sluggish
- Relevant areas: scan loop, buffers, timing, UI updates, radio state

## Observed Behavior

Scanning works for short sessions but becomes unreliable during longer runs.

## Expected Behavior

Scanning should continue predictably, report results, and recover from temporary radio or timing errors.

## Evidence Collected

```text
Scan loop runs continuously.
Result buffer grows without clear pruning.
UI refresh and scan processing share the same loop.
```

## Fault Map

```text
Long scan -> loop pressure -> shared scan/UI work -> buffer/timing stress -> dropped or delayed results
```

## Root Cause Hypotheses

| Rank | Hypothesis | Confidence | Test |
|---|---|---|---|
| 1 | Scan result buffer is not bounded or drained safely | Medium | Add counters and inspect growth |
| 2 | UI refresh blocks scan processing | Medium | Measure loop timing around UI updates |
| 3 | Radio state errors are not retried cleanly | Low | Add state transition logging |

## Recommended Patch

Add bounded buffering, explicit scan state transitions, and lightweight timing logs before changing radio behavior.

## Validation Steps

1. Run a short scan and capture baseline logs.
2. Run a long scan and capture buffer and loop timing metrics.
3. Confirm no unbounded growth.
4. Confirm scan state recovers after transient errors.

## Regression Prevention

Create a long-running scan test profile with expected counters and timeout thresholds.
