# Task 2 - Git Commands Log

## Commands Executed and Results

### 1. Check Git Status (initial)
```
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ./

nothing added to commit but untracked files present (use "git add" to track)
```

### 2. Stage All Files
```
$ git add .
```

### 3. Check Git Status (after staging)
```
$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   .gitignore
        new file:   index.html
```

### 4. List Files
```
$ ls
index.html      styles.css
```

### 5. List All Files (including hidden)
```
$ ls -a
.               ..              .gitignore      index.html      styles.css
```

### 6. Commit Changes
```
$ git commit -m "test gitignore"
[main e958f8a] test gitignore
 2 files changed, 12 insertions(+)
 create mode 100644 task2/.gitignore
 create mode 100644 task2/index.html
```
