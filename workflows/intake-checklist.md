# Intake Checklist

Use this workflow before deep analysis. The goal is to capture enough context to avoid guessing.

## Case Metadata

- [ ] Case title
- [ ] Date opened
- [ ] Operator
- [ ] Device, service, tool, or repository
- [ ] Severity estimate
- [ ] Current status

## System Context

- [ ] Device or board model
- [ ] Chipset or CPU architecture
- [ ] Firmware/software version
- [ ] Framework or runtime
- [ ] Toolchain version
- [ ] Operating system
- [ ] Build/upload command
- [ ] Relevant environment variables

## Observed Behavior

- [ ] Exact symptom
- [ ] When it started
- [ ] Frequency
- [ ] Reproduction steps
- [ ] Expected behavior
- [ ] Actual behavior
- [ ] Recent changes

## Evidence Package

- [ ] Full error output
- [ ] Logs from first failure through downstream symptoms
- [ ] Source files or config involved
- [ ] Dependency manifests and lockfiles
- [ ] Screenshots or photos, if useful
- [ ] Wiring or topology notes, if hardware is involved

## Safety Check

- [ ] Confirm the system is owned, open-source, or explicitly authorized for analysis.
- [ ] Remove credentials, private keys, tokens, and customer identifiers from shared logs.
- [ ] Identify actions that require human approval, such as flashing, destructive writes, production changes, or hardware modifications.

## Ready For Fault Mapping

Proceed when:

- the primary symptom is clear
- logs or source evidence are available
- expected behavior is known
- environment details are captured
- risky actions are identified
