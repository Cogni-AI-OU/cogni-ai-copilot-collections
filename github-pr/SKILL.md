---
name: github-pr
description: >-
  Skills for working with changes on a GitHub Pull Request.
  You must load this skill when working with changes on a pull request.
---
# github-pr Skill

Use this skill when interacting with pull requests, specifically to fetch
feedback, check build statuses, and retrieve inline annotations.

## When to Activate

- Working with changes on a pull request.
- Need to fetch PR comments, build status, or inline annotations.

## Fetching PR Information

### PR Comments

To fetch all comments on a pull request:

```bash
gh pr view <number> --json comments
```

### Build Status (Checks)

To see the current build status and CI checks:

```bash
gh pr checks <number>
```

To get structured JSON output of checks:

```bash
gh pr checks <number> --json name,status,conclusion,url
```

### Inline Annotations

Inline annotations are part of check runs. To fetch them, you first need the
check run IDs associated with the PR's head commit.

1. Get the head SHA and check run IDs:
   ```bash
   gh pr view <number> --json headRefOid
   # Then use the OID to get check runs
   gh api repos/:owner/:repo/commits/<headRefOid>/check-runs --jq '.check_runs[] | {id, name, status, conclusion}'
   ```

2. Fetch annotations for a specific check run ID:
   ```bash
   gh api repos/:owner/:repo/check-runs/<check_run_id>/annotations
   ```

## Related Skills

- **[gh-pr](../gh-pr/SKILL.md)**: For low-level `gh pr` command operations.
- **[github](../github/SKILL.md)**: For web-based PR interactions (.diff, .patch).
