# Patch Validation Workflow

Use this workflow after a patch has been implemented or proposed.

## Purpose

Validation proves that the original fault is resolved and that no obvious regression was introduced.

## Step 1: Restate The Patch

Record:

- target files or components
- change summary
- root cause addressed
- expected effect
- rollback plan

## Step 2: Validate The Original Failure

- [ ] Reproduce the original issue before patch, if possible.
- [ ] Apply the patch.
- [ ] Rerun the exact reproduction steps.
- [ ] Confirm the original symptom no longer appears.
- [ ] Capture logs or output proving the result.

## Step 3: Validate Nearby Behavior

Check:

- startup and shutdown
- error handling
- configuration loading
- dependency initialization
- connected peripherals or services
- expected performance or memory behavior

## Step 4: Regression Guard

Choose at least one:

- unit test
- integration test
- CI build check
- static check
- hardware-in-loop validation
- manual checklist
- log signature check

## Step 5: Document Results

```md
## Patch Under Test

## Original Failure

## Test Environment

## Commands Or Steps Run

## Results

## Evidence

## Regression Checks

## Remaining Risk

## Verdict
```

## Verdict Labels

- **Pass**: patch resolves the issue and regression checks passed
- **Partial**: primary issue improved but remaining risk exists
- **Fail**: issue remains or a new blocking issue appeared
- **Blocked**: validation could not run due to missing hardware, dependency, permission, or environment
