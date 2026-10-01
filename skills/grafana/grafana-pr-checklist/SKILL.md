---
name: grafana-pr-checklist
description: "Investigate or review Grafana bug fixes by tracing shared state, every relevant caller, alternate UI modes, and failure-to-recovery behavior before preparing a pull request."
---

# Grafana PR checklist

Trace the behavior beyond the file named in an issue before implementing or reviewing a Grafana fix.

## Required reference

Read [the original PR checklist](references/pr-checklist.md) when using this skill. It contains the complete investigation process, review questions, and pre-PR checklist.

## Apply the checklist

- Map every relevant state producer, consumer, and reset path.
- Search the changed component's callers, wrappers, and lower-level components for paths that bypass the proposed behavior.
- Inspect alternate layouts and feature-flagged paths that can affect the fix.
- Define expected failure, success, and recovery behavior for the affected paths. Place the behavior at the appropriate shared layer without duplicating global state in repeated UI.
- Check that user-facing error messages are accurate for every condition that can trigger them.
- Run relevant regression tests and the target repository's required checks. Repeat the important symbol searches and review the final diff for uncovered paths.
- Report what was verified and what remains uncertain before calling the fix complete.

## Interpret the example

The reference describes a historical datasource-error fix involving `dsError`, `QueryEditorRenderer`, `QueryEditorPanel`, and stacked queries. Treat these symbols and issue #130945 as a worked example. Verify current source before relying on their existence or relationships. Apply the checklist to the actual bug and the target repository's current contribution rules.
