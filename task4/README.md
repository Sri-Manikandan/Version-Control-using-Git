# Task 4 - Git Branching and Merge Conflict Resolution

This task demonstrates creating branches, making changes, merging branches, and resolving merge conflicts.

---

## Commands and Results

### 1. Stage and commit initial file

```bash
$ git add .
$ git commit -m "initial commit"
```
```
[main 1e4a764] initial commit
 1 file changed, 11 insertions(+)
 create mode 100644 task4/index.html
```

---

### 2. Create and switch to feature-1 branch

```bash
$ git checkout -b feature-1
```
```
Switched to a new branch 'feature-1'
```

---

### 3. Stage and commit changes on feature-1

```bash
$ git add .
$ git commit -m "feature 1 update"
```
```
[feature-1 0b13bae] feature 1 update
 1 file changed, 1 insertion(+), 1 deletion(-)
```

---

### 4. Switch back to main and create feature-2 branch

```bash
$ git checkout main
```
```
Switched to branch 'main'
```

```bash
$ git checkout -b feature-2
```
```
Switched to a new branch 'feature-2'
```

---

### 5. Stage and commit changes on feature-2

```bash
$ git add .
$ git commit -m "feature 2 update"
```
```
[feature-2 ee019ec] feature 2 update
 1 file changed, 1 insertion(+), 1 deletion(-)
```

---

### 6. Switch back to main and merge feature-1 (fast-forward)

```bash
$ git checkout main
```
```
Switched to branch 'main'
```

```bash
$ git merge feature-1
```
```
Updating 1e4a764..0b13bae
Fast-forward
 task4/index.html | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

> `feature-1` merged cleanly via fast-forward since main had no new commits after branching.

---

### 7. Merge feature-2 — conflict occurs

```bash
$ git merge feature-2
```
```
Auto-merging task4/index.html
CONFLICT (content): Merge conflict in task4/index.html
Automatic merge failed; fix conflicts and then commit the result.
```

> Both `feature-1` and `feature-2` modified the same line in `index.html`, causing a merge conflict.

---

### 8. Check status during conflict

```bash
$ git status
```
```
On branch main
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
```

---

### 9. Resolve conflict and stage the file

After manually editing `index.html` to resolve the conflict markers:

```bash
$ git add .
```

---

### 10. Commit the resolved merge

```bash
$ git commit -m "resolved merge conflict"
```
```
[main f1590ae] resolved merge conflict
```

---

### 11. Verify no remaining differences

```bash
$ git diff
```
```
(no output — working tree is clean)
```

```bash
$ git merge feature-2
```
```
Already up to date.
```

> Confirms `feature-2` is fully merged into `main`.

---

## Branch History (git log --oneline)

```
f1590ae resolved merge conflict
ee019ec feature 2 update
0b13bae feature 1 update
1e4a764 initial commit
```

---

## Key Concepts Covered

| Concept | Description |
|---|---|
| `git checkout -b <branch>` | Create and switch to a new branch |
| Fast-forward merge | Merge with no diverging history — pointer simply moves forward |
| Merge conflict | Occurs when two branches modify the same line differently |
| Conflict resolution | Manually edit the file, then `git add` and `git commit` |
