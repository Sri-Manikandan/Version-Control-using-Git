# Task 7 - Git Cherry-Pick Commands Log

## Commands and Results

### 1. Stage and commit initial file
```
$ git add .
$ git commit -m "initial commit"
[main 427e5c9] initial commit
 1 file changed, 11 insertions(+)
 create mode 100644 task7/index.html
```

### 2. Create and switch to feature-branch
```
$ git checkout -b feature-branch
Switched to a new branch 'feature-branch'
```

### 3. Commit Feature 1 on feature-branch
```
$ git add .
$ git commit -m "added feature 1"
[feature-branch 985fd08] added feature 1
 1 file changed, 1 insertion(+)
```

### 4. Commit Feature 2 on feature-branch
```
$ git add .
$ git commit -m "added feature 2"
[feature-branch 621a49a] added feature 2
 1 file changed, 1 insertion(+)
```

### 5. Switch to main and create hotfix-branch
```
$ git checkout main
Switched to branch 'main'
$ git checkout -b hotfix-branch
Switched to a new branch 'hotfix-branch'
```

### 6. Commit hotfix on hotfix-branch
```
$ git add .
$ git commit -m "hotfix applied"
[hotfix-branch 495e7ce] hotfix applied
 1 file changed, 1 insertion(+)
```

### 7. Switch to feature-branch and view log
```
$ git checkout feature-branch
Switched to branch 'feature-branch'
$ git log --oneline
621a49a (HEAD -> feature-branch) added feature 2
985fd08 added feature 1
427e5c9 (main) initial commit
c68d0c1 stash fixed
94aea1c first commit
4cc8bfb (origin/main) add README with git interactive rebase commands log for task5
dd6b005 second commit
bb05fcb first commit
ca19fbf add README with git branching and merge conflict commands log for task4
f1590ae resolved merge conflict
ee019ec (feature-2) feature 2 update
0b13bae (feature-1) feature 1 update
1e4a764 initial commit
c252af7 add README with git commands log for task3
1989b61 Revert "commit 2"
6dbe37d commit 2
03730fd commit 1
464e6bb add README with git commands log for task2
e958f8a test gitignore
155149d added readme for task1
0d18929 (feature/changing-index-html) new feature tested and committed
```

### 8. Switch back to hotfix-branch
```
$ git checkout hotfix-branch
Switched to branch 'hotfix-branch'
```

### 9. Cherry-pick Feature 1 commit onto hotfix-branch
```
$ git cherry-pick 985fd08
Auto-merging task7/index.html
CONFLICT (content): Merge conflict in task7/index.html
error: could not apply 985fd08... added feature 1
hint: After resolving the conflicts, mark them with
hint: "git add/rm <pathspec>", then run
hint: "git cherry-pick --continue".
hint: You can instead skip this commit with "git cherry-pick --skip".
hint: To abort and get back to the state before "git cherry-pick",
hint: run "git cherry-pick --abort".
hint: Disable this message with "git config set advice.mergeConflict false"
```

### 10. Resolve conflict, stage, and continue cherry-pick
```
$ git add .
$ git cherry-pick --continue
[hotfix-branch e5dc141] added feature 1
 Date: Mon Mar 30 21:56:35 2026 +0530
 1 file changed, 1 insertion(+), 1 deletion(-)
```
