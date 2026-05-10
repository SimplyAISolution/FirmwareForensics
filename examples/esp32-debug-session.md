# ESP32 Debug Session Example

## Summary

An ESP32 sketch fails to compile because program storage exceeds the selected partition capacity.

## System Context

- Device: ESP32 development board
- Framework: Arduino
- Symptom: compile fails during linking or size check
- Recent change: BLE, Wi-Fi, web server, and SD logging added together

## Observed Behavior

Compiler output reports program storage above the available limit.

## Expected Behavior

Firmware should compile and fit within the configured flash partition.

## Evidence Collected

```text
Sketch uses 1349012 bytes (102%) of program storage space. Maximum is 1310720 bytes.
```

## Fault Map

```text
Build failure -> size check -> app partition -> program too large -> partition/library pressure
```

## Root Cause Hypotheses

| Rank | Hypothesis | Confidence | Test |
|---|---|---|---|
| 1 | Selected partition scheme leaves too little app space | High | Switch to larger app partition and rebuild |
| 2 | Heavy libraries increased binary size | High | Temporarily disable modules and compare size |
| 3 | Debug symbols or logging are bloating build | Medium | Compare release optimization settings |

## Recommended Patch

Use a larger app partition if OTA/filesystem requirements allow it, then reduce optional library weight if the binary still exceeds target size.

## Validation Steps

1. Rebuild with the selected board and partition scheme.
2. Confirm program storage is below the maximum.
3. Flash the board.
4. Capture serial boot logs.
5. Exercise BLE, Wi-Fi, web server, and SD logging startup.

## Regression Prevention

Add a build-size check to CI or document a maximum acceptable firmware size for the target board profile.
