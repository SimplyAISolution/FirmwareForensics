# Raspberry Pi Service Error Example

## Summary

A Python service works when launched manually but fails after reboot under systemd.

## System Context

- Device: Raspberry Pi
- Runtime: Python service
- Process manager: systemd
- Symptom: service fails on boot but works from an interactive shell

## Observed Behavior

The service exits immediately after reboot. Manual execution from the project directory succeeds.

## Expected Behavior

The service should start automatically after boot.

## Evidence Collected

```text
ModuleNotFoundError: No module named 'app'
WorkingDirectory not set in service file
```

## Fault Map

```text
Boot start -> systemd unit -> wrong working directory -> Python import path failure -> service exits
```

## Root Cause Hypotheses

| Rank | Hypothesis | Confidence | Test |
|---|---|---|---|
| 1 | Missing WorkingDirectory in unit file | High | Add WorkingDirectory and restart |
| 2 | Virtual environment not used by ExecStart | Medium | Check ExecStart path |
| 3 | Environment variables missing under systemd | Medium | Compare shell env to unit env |

## Recommended Patch

Set `WorkingDirectory` and use the virtual environment Python executable in `ExecStart`.

## Validation Steps

1. Run `systemctl daemon-reload`.
2. Restart the service.
3. Check `systemctl status`.
4. Reboot the device.
5. Confirm the service starts without manual intervention.

## Regression Prevention

Add a documented systemd unit template and a reboot validation checklist.
