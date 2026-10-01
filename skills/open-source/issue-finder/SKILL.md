---
name: issue-finder
description: "Find open-source GitHub issues to contribute to and verify that they are available, still relevant, and realistically solvable before recommending them."
---

# Issue Finder

When I ask you to find an open-source GitHub issue for me to work on, do not recommend an issue until you have thoroughly verified that it is genuinely available.
Before recommending any issue:
1. Open and read the full issue, comments, timeline, labels, assignees, and linked references.
2. Search open PRs by exact issue number.
3. Search open PRs semantically using the issue title, error message, affected function names, and likely fix keywords.
4. Search repository branches containing the issue number or relevant keywords.
5. Search recent commits for fixes that may already have landed on main.
6. Check whether the bug is already fixed on the current default branch, even if the issue itself remains open.
7. Check comments for anyone saying they are working on it, planning a PR, or asking to be assigned.
8. Check older related issues/PRs to understand whether the proposed fix is actually still needed.
9. Inspect the current source code enough to identify the likely root cause and confirm the issue is realistically solvable.
10. Prefer issues that are fresh, unassigned, localized, testable, and likely to produce a clean maintainable PR.
