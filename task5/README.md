# Task 5 - Git Interactive Rebase Commands Log

## Commands Executed

```bash
# Stage and commit initial file
git add .
git commit -m "first commit"

# Stage and commit next line addition
git add .
git commit -m "added next line"

# Stage and commit bug fix
git add .
git commit -m "bug fix"

# Stage and commit typo fix
git add .
git commit -m "final changes typo"

# View commit history (failed attempt with typo)
git log --online
# fatal: unrecognized argument: --online

# View commit history (correct flag)
git log --oneline

# Squash last 4 commits interactively into 2 commits
git rebase -i HEAD~4

# View updated commit history after rebase
git log --oneline
```

## What Happened

- Made 4 individual commits: `first commit`, `added next line`, `bug fix`, `final changes typo`
- Used `git rebase -i HEAD~4` to interactively squash/reword the last 4 commits
- After rebase, the 4 commits were squashed into 2 cleaner commits:
  - `bb05fcb` - first commit
  - `dd6b005` - second commit
