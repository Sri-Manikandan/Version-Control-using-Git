# Task 8 - Git Hooks Command Log

## Overview
This task demonstrates setting up a Git `pre-commit` hook that blocks commits containing `console.log` statements.

---

## Commands and Results

### 1. Initial Commit
```bash
$ git add .
$ git commit -m "initial commit"
[hotfix-branch adbee2b] initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 task8/app.js
```

---

### 2. Navigate to Hooks Directory
```bash
$ cd ..
$ cd .git/hooks
$ ls
applypatch-msg.sample           post-update.sample              pre-merge-commit.sample         pre-receive.sample              sendemail-validate.sample
commit-msg.sample               pre-applypatch.sample           pre-push.sample                 prepare-commit-msg.sample       update.sample
fsmonitor-watchman.sample       pre-commit.sample               pre-rebase.sample               push-to-checkout.sample
```

---

### 3. Create and Configure Pre-commit Hook
```bash
$ touch pre-commit
$ chmod +x pre-commit
$ vim pre-commit
```
> Edited the hook to block commits containing `console.log` statements.

---

### 4. First Commit Attempt — Blocked (console.log in app.js)
```bash
$ cd ../../task8
$ git add .
$ git commit -m "testing hooks"
Running pre-commit checks...
./task8/app.js:console.log('Hello world')
./.git/hooks/pre-commit:# Example: prevent committing console.log
./.git/hooks/pre-commit:if grep -r "console.log" .; then
./.git/hooks/pre-commit:  echo "❌ Commit blocked: Remove console.log statements"
❌ Commit blocked: Remove console.log statements
```

---

### 5. Second Commit Attempt — Still Blocked
```bash
$ git add .
$ git commit -m "adjusting code for hooks"
Running pre-commit checks...
./.git/hooks/pre-commit:# Example: prevent committing console.log
./.git/hooks/pre-commit:if grep -r "console.log" .; then
./.git/hooks/pre-commit:  echo "❌ Commit blocked: Remove console.log statements"
❌ Commit blocked: Remove console.log statements
```
> **Note:** The `grep` was scanning the entire repo including the hook file itself, causing a false positive even after removing `console.log` from `app.js`.

---

### 6. Third and Fourth Attempts — Still Blocked
```bash
$ git add app.js
$ git status
On branch hotfix-branch
Changes to be committed:
        modified:   app.js
Untracked files:
        ../task6/README.md

$ git commit -m "adjusting code for hooks"
Running pre-commit checks...
❌ Commit blocked: Remove console.log statements
```
> Staging only `app.js` did not help — the hook still matched its own file during grep.

---

### 7. Fix the Hook (Narrow grep scope to exclude itself)
```bash
$ cd ../.git/hooks
$ vim pre-commit
$ cd ../../task8
```
> Updated the grep command in the hook to exclude the `.git/hooks` directory so it no longer triggers on its own content.

---

### 8. Final Successful Commit
```bash
$ git add .
$ git commit -m "adjusting code for hooks"
Running pre-commit checks...
✅ All checks passed
[hotfix-branch 7d9afae] adjusting code for hooks
 1 file changed, 7 insertions(+), 1 deletion(-)
```

---

## Summary

| Step | Command | Result |
|------|---------|--------|
| 1 | `git commit -m "initial commit"` | Success — created `app.js` |
| 2 | Navigate to `.git/hooks` | Listed existing sample hooks |
| 3 | `touch pre-commit` + `chmod +x` + `vim` | Created and configured `pre-commit` hook |
| 4 | `git commit -m "testing hooks"` | Blocked — `console.log` found in `app.js` |
| 5 | `git commit -m "adjusting code for hooks"` | Blocked — hook's grep matched itself |
| 6 | Multiple attempts with `git add app.js` | Blocked — false positive from hook file |
| 7 | `vim pre-commit` (fix grep scope) | Fixed hook to exclude `.git/hooks` directory |
| 8 | `git commit -m "adjusting code for hooks"` | Success — all checks passed |

---

## Key Takeaway
When writing a `pre-commit` hook that uses `grep -r` to scan the repo, always **exclude the `.git/` directory** (or narrow the scope) to prevent the hook from matching its own content and causing false positives.
