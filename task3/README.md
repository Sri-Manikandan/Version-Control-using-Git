# Task 3 - Git Commands Log

## Commands and Results

### 1. Stage all changes
```
$ git add .
```

---

### 2. Create commit 1
```
$ git commit -m "commit 1"
[main 03730fd] commit 1
 1 file changed, 12 insertions(+)
 create mode 100644 task3/index.html
```

---

### 3. Check status (modified file detected)
```
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
```

---

### 4. Restore index.html to last committed state
```
$ git restore index.html
```

---

### 5. Stage all changes
```
$ git add .
```

---

### 6. Create commit 2
```
$ git commit -m "commit 2"
[main 6dbe37d] commit 2
 1 file changed, 1 insertion(+)
```

---

### 7. Revert commit 2 (creates a new revert commit)
```
$ git revert HEAD
[main 1989b61] Revert "commit 2"
 1 file changed, 1 deletion(-)
```

---

### 8. View commit history
```
$ git log
commit 1989b61d07b3e92b33fc8355459ff9643b7a0e5d (HEAD -> main)
Author: Synergeek Technologies <synergeektechnologies@gmail.com>
Date:   Mon Mar 30 14:32:54 2026 +0530

    Revert "commit 2"

    This reverts commit 6dbe37ddeacfbca79b13a2b9ac982b5394b7710d.

commit 6dbe37ddeacfbca79b13a2b9ac982b5394b7710d
Author: Synergeek Technologies <synergeektechnologies@gmail.com>
Date:   Mon Mar 30 14:32:48 2026 +0530

    commit 2

commit 03730fd03399b049268335acf87581eea49de2f4
Author: Synergeek Technologies <synergeektechnologies@gmail.com>
Date:   Mon Mar 30 14:31:52 2026 +0530

    commit 1

commit 464e6bb4f1edb8cefa787ea7daac07823a5e9141 (origin/main)
```

---

### 9. Stage all changes
```
$ git add .
```

---

### 10. Create a reset commit
```
$ git commit -m "reset commit"
[main 61b1ba4] reset commit
 1 file changed, 1 insertion(+)
```

---

### 11. Hard reset to 1 commit before HEAD (discards reset commit)
```
$ git reset --hard HEAD~1
HEAD is now at 1989b61 Revert "commit 2"
```

---

## Summary

| Command | Purpose |
|---|---|
| `git add .` | Stage all changes |
| `git commit -m "<message>"` | Create a new commit |
| `git status` | Check working tree status |
| `git restore <file>` | Discard changes in working directory |
| `git revert HEAD` | Create a new commit that undoes the last commit |
| `git log` | View commit history |
| `git reset --hard HEAD~1` | Discard the last commit and all its changes permanently |
