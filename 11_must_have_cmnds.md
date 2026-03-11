
---

## 1. git add

### Definition

`git add` moves changes from the **working directory to the staging area**.

It tells Git that **these changes should be included in the next commit**.

### Syntax

```bash
git add <file-name>
```

Add all files:

```bash
git add .
```

### Example

```bash
git add index.html
```

### Interview Explanation

> git add is used to move changes from the working directory to the staging area before committing them to the repository.

---

# 2. git commit

### Definition

`git commit` saves the **staged changes into the Git repository** as a snapshot.

Each commit contains:

* commit ID (SHA hash)
* author
* timestamp
* commit message

### Syntax

```bash
git commit -m "message"
```

### Example

```bash
git commit -m "Added login feature"
```

### Interview Explanation

> git commit records staged changes into the repository and creates a new version of the project.

---

# 3. git log

### Definition

`git log` shows the **commit history of the repository**.

### Syntax

```bash
git log
```

### Example Output

```
commit 83a9e12
Author: Umesh Raut
Date:   Mar 6 2026
Message: Added login page
```

### Useful Options

Short version:

```bash
git log --oneline
```

### Interview Explanation

> git log displays the history of commits including commit IDs, author details, dates, and commit messages.

---

# 4. git diff

### Definition

`git diff` shows the **difference between file versions**.

It compares:

* working directory vs staging
* staging vs last commit

### Syntax

```bash
git diff
```

### Example

```bash
git diff index.html
```

Output example:

```
- old line
+ new line
```

### Interview Explanation

> git diff shows the changes between different versions of files.

---

# 5. git show

### Definition

`git show` displays **detailed information about a specific commit**.

It shows:

* commit metadata
* author
* date
* code changes

### Syntax

```bash
git show <commit-id>
```

Example:

```bash
git show a3f7c1
```

### Interview Explanation

> git show displays detailed information about a specific commit including the changes made.

---

# 6. git rm

### Definition

`git rm` removes files from both:

* working directory
* Git repository

### Syntax

```bash
git rm <file-name>
```

Example

```bash
git rm test.txt
```

Then commit the change:

```bash
git commit -m "Removed test file"
```

### Interview Explanation

> git rm removes a file from the working directory and stages the deletion for the next commit.

---

# 7. git mv

### Definition

`git mv` moves or renames a file in the repository.

### Syntax

```bash
git mv oldname newname
```

### Example

```bash
git mv file1.txt file2.txt
```

Then commit:

```bash
git commit -m "Renamed file"
```

### Interview Explanation

> git mv is used to rename or move files within the Git repository.

---

# Git Workflow Using These Commands

Typical workflow:

```
Modify files
    ↓
git add
    ↓
git commit
    ↓
git log
```

Other operations:

```
git diff → check changes
git show → see commit details
git rm → delete files
git mv → rename files
```

---

# Quick Interview Cheat Sheet

| Command    | Purpose                    |
| ---------- | -------------------------- |
| git add    | Add files to staging area  |
| git commit | Save changes to repository |
| git log    | View commit history        |
| git diff   | Show file differences      |
| git show   | Show details of a commit   |
| git rm     | Remove file                |
| git mv     | Rename or move file        |

---

