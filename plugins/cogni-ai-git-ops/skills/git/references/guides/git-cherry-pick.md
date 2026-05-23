<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

# Git Cherry-Pick (Advanced)

Apply specific commits from one branch to another without merging the whole branch.

## Core Process

- **Single commit**: `git cherry-pick <commit-sha>`
- **Multiple commits**: `git cherry-pick <sha-A>^..<sha-B>`
- **No commit (stage only)**: `git cherry-pick -n <commit-sha>`
