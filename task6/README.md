# Task 6 - Git Stash Commands Log

## Commands and Results

### 1. Stage all files
```bash
$ git add .
```

### 2. Commit the staged files
```bash
$ git commit -m "first commit"
[main 94aea1c] first commit
 1 file changed, 11 insertions(+)
 create mode 100644 task6/index.html
```

### 3. Check the working tree status
```bash
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
```

### 4. Stash the current changes
```bash
$ git stash
Saved working directory and index state WIP on main: 94aea1c first commit
```

### 5. Create and switch to a new branch
```bash
$ git checkout -b bugfix-branch
Switched to a new branch 'bugfix-branch'
```

### 6. Stage all files on the new branch
```bash
$ git add .
```

### 7. Commit the bug fix
```bash
$ git commit -m "bug fixed"
[bugfix-branch 0a18643] bug fixed
 1 file changed, 1 insertion(+)
```

### 8. Switch back to main branch
```bash
$ git checkout main
Switched to branch 'main'
```

### 9. List all stashes
```bash
$ git stash list
stash@{0}: WIP on main: 94aea1c first commit
```

### 10. Pop the stash to restore changes
```bash
$ git stash pop
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (6675a9883735fe35c9810cb959ebb3e23752d8b5)
```

### 11. Stage the restored changes
```bash
$ git add .
```

### 12. Commit the restored stash changes
```bash
$ git commit -m "stash fixed"
[main c68d0c1] stash fixed
 1 file changed, 1 insertion(+)
```
