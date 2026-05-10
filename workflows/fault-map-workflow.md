# Fault Map Workflow

Use this workflow to convert raw symptoms into traceable hypotheses.

## Purpose

A fault map connects:

```text
Symptom -> Trigger -> Component -> Code/Config Path -> Root Cause -> Patch -> Validation
```

## Step 1: Define The Symptom

Record:

- exact failure
- user-visible impact
- when it occurs
- whether it is deterministic or intermittent
- whether a workaround exists

## Step 2: Capture Evidence

Create an evidence table:

| ID | Evidence | Source | Why It Matters |
|---|---|---|---|
| E1 |  |  |  |

## Step 3: Separate Facts And Assumptions

Facts:

- directly observed
- supported by logs, code, config, measurements, or commands

Assumptions:

- plausible but unverified
- inherited from naming, memory, or expected behavior

## Step 4: Map The Failure Path

Trace:

- trigger
- entry point
- affected component
- downstream symptoms
- error handling path
- retry or recovery behavior

## Step 5: Generate Hypotheses

| Rank | Hypothesis | Evidence | Confidence | Test |
|---|---|---|---|---|
| 1 |  |  |  |  |

## Step 6: Pick The Next Check

Choose the check that:

- is safe
- is fast
- gives the strongest signal
- reduces the largest uncertainty

## Step 7: Produce The Fault Map

```md
## Symptom

## Trigger

## Affected Component

## Evidence

## Failure Path

## Hypotheses

## Most Likely Cause

## Next Diagnostic Check

## Patch Direction

## Validation Method
```
