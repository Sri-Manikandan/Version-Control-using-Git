# Task 10 - Git Advanced Workflow: Rebase, Reflog & Recovery

## Command Log with Results

### 1. Stage and commit initial files

```
$ git add .
$ git commit -m "initial commit"
[main 281a26c] initial commit
 1 file changed, 11 insertions(+)
 create mode 100644 task10/index.html
```

---

### 2. Create and switch to feature-auth branch

```
$ git checkout -b feature-auth
Switched to a new branch 'feature-auth'
```

---

### 3. Commit auth feature versions

```
$ git commit -am "Add auth v1"
[feature-auth f46588e] Add auth v1
 1 file changed, 1 insertion(+)

$ git commit -am "Add auth v2"
[feature-auth 7670bb5] Add auth v2
 1 file changed, 1 insertion(+)
```

---

### 4. Switch to main and create bugfix-login branch

```
$ git checkout main
Switched to branch 'main'

$ git checkout -b bugfix-login
Switched to a new branch 'bugfix-login'

$ git commit -am "Fix login issue"
[bugfix-login 34d54c1] Fix login issue
 1 file changed, 1 insertion(+)
```

---

### 5. Create release-v1 branch and merge bugfix-login

```
$ git checkout main
Switched to branch 'main'

$ git checkout -b release-v1
Switched to a new branch 'release-v1'

$ git merge bugfix-login
Updating 281a26c..34d54c1
Fast-forward
 task10/index.html | 1 +
 1 file changed, 1 insertion(+)
```

---

### 6. Interactive rebase on feature-auth to squash commits

```
$ git checkout feature-auth
Switched to branch 'feature-auth'

$ git rebase -i HEAD~2
[detached HEAD 35aefd4] Add complete auth feature
 Date: Mon Mar 30 22:42:16 2026 +0530
 1 file changed, 1 insertion(+)
[detached HEAD 5b5af0a] Add complete auth feature
 Date: Mon Mar 30 22:42:16 2026 +0530
 1 file changed, 2 insertions(+)
Successfully rebased and updated refs/heads/feature-auth.
```

---

### 7. View log after rebase

```
$ git log
commit 5b5af0a01c5a6e6038f958bd5f68cd5bb70a4a4e (HEAD -> feature-auth)
    Add complete auth feature
    Add auth v2

commit 281a26c7d08747db2ca27659d82fab9fde949cb8 (main)
    initial commit

commit e91f8152bda2673a568c57c66a377f1cd35bc077 (origin/main)
    add README with command log for task9 git workflow
```

---

### 8. Push feature-auth to remote

```
$ git push origin feature-auth
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 8 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (8/8), 869 bytes | 869.00 KiB/s, done.
Total 8 (delta 3), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (3/3), completed with 1 local object.
To https://github.com/Sri-Manikandan/Version-Control-using-Git.git
 * [new branch]      feature-auth -> feature-auth
```

---

### 9. Rebase errors and recovery

```
$ git rebase -i HEAD~1
error: cannot 'squash' without a previous commit

$ git rebase -i HEAD~2
fatal: It seems that there is already a rebase-merge directory...

$ git rebase --continue
error: cannot 'squash' without a previous commit

$ git rebase --edit-todo
error: cannot 'squash' without a previous commit

$ git rebase --continue
Successfully rebased and updated refs/heads/feature-auth.
```

---

### 10. Squash commits via rebase (HEAD~2)

```
$ git rebase -i HEAD~2
[detached HEAD 6eb318d] initial commit
 Date: Mon Mar 30 22:41:46 2026 +0530
 1 file changed, 13 insertions(+)
 create mode 100644 task10/index.html
Successfully rebased and updated refs/heads/feature-auth.

$ git log --oneline
6eb318d (HEAD -> feature-auth) initial commit
e91f815 (origin/main) add README with command log for task9 git workflow
046bccd Merge pull request #1 from Sri-Manikandan/feature-login
...
```

---

### 11. Force push after rebase (history rewrite)

```
$ git push origin feature-auth
! [rejected] feature-auth -> feature-auth (non-fast-forward)
error: failed to push some refs to 'https://github.com/...'
hint: Updates were rejected because the tip of your current branch is behind

$ git push origin feature-auth --force
Enumerating objects: 5, done.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 540 bytes | 540.00 KiB/s, done.
To https://github.com/Sri-Manikandan/Version-Control-using-Git.git
 + 5b5af0a...6eb318d feature-auth -> feature-auth (forced update)
```

---

### 12. Hard reset and recovery with reflog

```
$ git reset --hard HEAD~1
HEAD is now at e91f815 add README with command log for task9 git workflow

$ git reflog
e91f815 HEAD@{0}: reset: moving to HEAD~1
6eb318d HEAD@{1}: rebase (finish): returning to refs/heads/feature-auth
6eb318d HEAD@{2}: rebase (squash): initial commit
281a26c HEAD@{3}: rebase (start): checkout HEAD~2
5b5af0a HEAD@{4}: rebase (finish): returning to refs/heads/feature-auth
...

$ git reset --hard def456
fatal: ambiguous argument 'def456': unknown revision or path not in the working tree.

$ git reset --hard 6eb318d
HEAD is now at 6eb318d initial commit
```

---

### 13. Final log and push

```
$ git log --oneline
6eb318d (HEAD -> feature-auth, origin/feature-auth) initial commit
e91f815 (origin/main) add README with command log for task9 git workflow
046bccd Merge pull request #1 from Sri-Manikandan/feature-login
...

$ git push --force
fatal: The current branch feature-auth has no upstream branch.
To push the current branch and set the remote as upstream, use
    git push --set-upstream origin feature-auth

$ git push origin feature-auth --force
Everything up-to-date
```

---

## Key Concepts Covered

- **Interactive Rebase** (`git rebase -i`): Squash, reword, and reorder commits
- **Reflog** (`git reflog`): View history of all HEAD movements, including resets
- **Recovery** (`git reset --hard <hash>`): Restore to any previous state using reflog hashes
- **Force Push** (`git push --force`): Required after rewriting history with rebase
- **Branch Strategy**: `feature-auth`, `bugfix-login`, `release-v1` branching workflow
