<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

# Git Reflog Recovery

Recover lost commits, branches, or undo a destructive operation (like a bad hard reset).

## Core Process

- **View history of HEAD movements**: `git reflog`
- **Identify the target commit SHA** (e.g., `HEAD@{2}`).
- **Restore state**: `git reset --hard <sha>` or create a branch: `git branch <branch-name> <sha>`.
