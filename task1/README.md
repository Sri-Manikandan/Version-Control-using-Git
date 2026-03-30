# Git Version Control - Task 1

## Commands Executed and Results

### 1. Stage all files
```bash
git add .
```
Stages all files in the current directory for commit.

---

### 2. Initial Commit
```bash
git commit -m "created index.html file"
```
**Result:**
```
[main (root-commit) a918250] created index.html file
 1 file changed, 11 insertions(+)
 create mode 100644 task1/index.html
```

---

### 3. Create a New Feature Branch
```bash
git branch feature/changing-index-html
```
Creates a new branch named `feature/changing-index-html`.

---

### 4. Switch to the Feature Branch
```bash
git checkout feature/changing-index-html
```
**Result:**
```
Switched to branch 'feature/changing-index-html'
```

---

### 5. Stage Changes on Feature Branch
```bash
git add .
```
Stages the modified files on the feature branch.

---

### 6. Commit Feature Changes
```bash
git commit -m "new feature tested and committed"
```
**Result:**
```
[feature/changing-index-html 0d18929] new feature tested and committed
 1 file changed, 1 insertion(+)
```

---

### 7. Switch Back to Main Branch
```bash
git checkout main
```
**Result:**
```
Switched to branch 'main'
```

---

### 8. Merge Feature Branch into Main
```bash
git merge feature/changing-index-html
```
**Result:**
```
Updating a918250..0d18929
Fast-forward
 task1/index.html | 1 +
 1 file changed, 1 insertion(+)
```
A **fast-forward merge** was performed since there were no diverging commits.

---

### 9. View Commit History
```bash
git log
```
**Result:**
```
commit 0d18929e95df3f31569f28817cf16899d71841dc (HEAD -> main, feature/changing-index-html)
Author: Synergeek Technologies <synergeektechnologies@gmail.com>
Date:   Mon Mar 30 10:19:30 2026 +0530

    new feature tested and committed

commit a918250769a569e6ca28b15eb0cdcdecca5a0130
Author: Synergeek Technologies <synergeektechnologies@gmail.com>
Date:   Mon Mar 30 10:16:36 2026 +0530

    created index.html file
```

---

## Summary

| Step | Command | Purpose |
|------|---------|---------|
| 1 | `git add .` | Stage files for initial commit |
| 2 | `git commit -m "created index.html file"` | Initial commit on main |
| 3 | `git branch feature/changing-index-html` | Create feature branch |
| 4 | `git checkout feature/changing-index-html` | Switch to feature branch |
| 5 | `git add .` | Stage feature changes |
| 6 | `git commit -m "new feature tested and committed"` | Commit on feature branch |
| 7 | `git checkout main` | Switch back to main |
| 8 | `git merge feature/changing-index-html` | Merge feature into main |
| 9 | `git log` | View commit history |
