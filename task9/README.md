# Task 9 - Git Branch and Pull Request Workflow

## Command Log

### 1. Stage all files
```
$ git add .
```

### 2. Create initial commit
```
$ git commit -m "initial commit"
```
**Output:**
```
[main e240888] initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 task9/app.txt
```

### 3. Create and switch to a new branch
```
$ git checkout -b feature-login
```
**Output:**
```
Switched to a new branch 'feature-login'
```

### 4. Add content to app.txt
```
$ echo "Login feature" >> app.txt
```

### 5. Stage the changes
```
$ git add .
```

### 6. Commit the feature changes
```
$ git commit -m "added login feature"
```
**Output:**
```
[feature-login 65396c0] added login feature
 1 file changed, 1 insertion(+), 1 deletion(-)
```

### 7. Push feature branch to remote
```
$ git push origin feature-login
```
**Output:**
```
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (8/8), 634 bytes | 634.00 KiB/s, done.
Total 8 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 1 local object.
remote:
remote: Create a pull request for 'feature-login' on GitHub by visiting:
remote:      https://github.com/Sri-Manikandan/Version-Control-using-Git/pull/new/feature-login
remote:
To https://github.com/Sri-Manikandan/Version-Control-using-Git.git
 * [new branch]      feature-login -> feature-login
```

### 8. Switch back to main branch
```
$ git checkout main
```
**Output:**
```
Switched to branch 'main'
```

### 9. Pull latest changes from remote main
```
$ git pull origin main
```
**Output:**
```
remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (1/1), 897 bytes | 448.00 KiB/s, done.
From https://github.com/Sri-Manikandan/Version-Control-using-Git
 * branch            main       -> FETCH_HEAD
   7b43242..046bccd  main       -> origin/main
Updating e240888..046bccd
Fast-forward
 task9/app.txt | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```
