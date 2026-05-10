# Release Review Workflow

Use this workflow before publishing a fix, flashing firmware broadly, shipping automation, or sharing a report.

## Scope Review

- [ ] The change addresses a mapped fault.
- [ ] The patch does not include unrelated refactors.
- [ ] Risky configuration, flash, deployment, or security changes are called out.
- [ ] Rollback is documented.

## Evidence Review

- [ ] Root cause is tied to logs, code, config, or measurements.
- [ ] Confidence level is stated.
- [ ] Remaining unknowns are listed.
- [ ] Sensitive data has been removed from shared artifacts.

## Validation Review

- [ ] Original failure was reproduced or clearly documented as not reproducible.
- [ ] Validation steps were run.
- [ ] Results were captured.
- [ ] Regression guard is in place or a manual fallback is documented.

## Documentation Review

- [ ] Patch plan is complete.
- [ ] Test report is complete.
- [ ] Operator notes are clear enough to repeat.
- [ ] Client-safe summary is separated from private technical detail when needed.

## Release Verdict

```md
## Release Candidate

## Change Summary

## Risk Level

## Validation Evidence

## Rollback Plan

## Remaining Unknowns

## Approval
```

## Approval Labels

- **Approved**: ready to publish, flash, merge, or share
- **Approved With Notes**: acceptable with documented caveats
- **Blocked**: missing evidence, validation, rollback, or approval
