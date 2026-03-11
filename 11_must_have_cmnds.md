
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

Below are **40 essential Git commands every DevOps engineer should know**, grouped according to the **real workflow used in CI/CD pipelines** with tools like Git, GitHub, GitLab, and Jenkins.

This structure mirrors how Git is used in **real DevOps environments**.

---

# Git Architecture (DevOps Perspective)

Typical flow in a development pipeline:

```
Developer
   ↓
Working Directory
   ↓
Staging Area
   ↓
Local Repository
   ↓
Remote Repository (GitHub / GitLab)
   ↓
CI/CD Pipeline Trigger
```

Commands move code through these stages.

---

# 1. Repository Initialization Commands

### 1. Initialize a repository

```bash
git init
```

Creates a new Git repository.

---

### 2. Clone a repository

```bash
git clone https://github.com/user/project.git
```

Downloads a remote repository to your machine.

---

### 3. Shallow clone (CI/CD optimization)

```bash
git clone --depth 1 repo-url
```

Downloads only the latest commit.

Used in CI pipelines to reduce cloning time.

---

# 2. Repository Information Commands

### 4. Check repository status

```bash
git status
```

Shows modified, staged, and untracked files.

---

### 5. View commit history

```bash
git log
```

---

### 6. Compact commit history

```bash
git log --oneline
```

---

### 7. Show changes

```bash
git diff
```

Displays differences between files.

---

# 3. Staging Commands

### 8. Add file to staging

```bash
git add file.txt
```

---

### 9. Add all files

```bash
git add .
```

---

### 10. Remove file

```bash
git rm file.txt
```

---

### 11. Move or rename file

```bash
git mv oldname newname
```

---

# 4. Commit Commands

### 12. Commit changes

```bash
git commit -m "Added login feature"
```

---

### 13. Amend last commit

```bash
git commit --amend
```

Fix commit message or add files.

---

### 14. Show commit details

```bash
git show commit-id
```

---

# 5. Branch Management Commands

### 15. Create branch

```bash
git branch feature-login
```

---

### 16. Switch branch

```bash
git checkout feature-login
```

---

### 17. Create and switch branch

```bash
git checkout -b feature-login
```

---

### 18. List branches

```bash
git branch
```

---

### 19. Delete branch

```bash
git branch -d feature-login
```

---

# 6. Remote Repository Commands

### 20. Add remote repository

```bash
git remote add origin repo-url
```

---

### 21. Show remote repositories

```bash
git remote -v
```

---

### 22. Push code

```bash
git push origin main
```

Triggers CI/CD pipelines.

---

### 23. Pull latest code

```bash
git pull origin main
```

---

### 24. Fetch updates

```bash
git fetch origin
```

Downloads changes without merging.

---

# 7. Merge and Rebase Commands

### 25. Merge branch

```bash
git merge feature-login
```

---

### 26. Rebase branch

```bash
git rebase main
```

---

### 27. Interactive rebase (squash commits)

```bash
git rebase -i HEAD~3
```

---

# 8. Undo and Recovery Commands

### 28. Undo last commit (keep changes)

```bash
git reset --soft HEAD~1
```

---

### 29. Delete commit and changes

```bash
git reset --hard HEAD~1
```

---

### 30. Revert commit safely

```bash
git revert commit-id
```

Used in production.

---

### 31. View reference log

```bash
git reflog
```

Recover lost commits.

---

# 9. Advanced DevOps Commands

### 32. Stash temporary changes

```bash
git stash
```

Restore later

```bash
git stash pop
```

---

### 33. Cherry pick commit

```bash
git cherry-pick commit-id
```

---

### 34. Find bug commit

```bash
git bisect
```

Binary search through commits.

---

### 35. Show who modified code

```bash
git blame file.js
```

---

### 36. Create tag (release)

```bash
git tag v1.0
```

Push tag

```bash
git push origin v1.0
```

---

# 10. Repository Optimization Commands

### 37. Garbage collection

```bash
git gc
```

Cleans unused objects.

---

### 38. Clean untracked files

```bash
git clean -f
```

---

### 39. Verify repository

```bash
git fsck
```

Checks repository integrity.

---

### 40. Work with submodules

```bash
git submodule add repo-url
```

---

# Real DevOps CI/CD Workflow

Example pipeline using Git with GitHub Actions or Jenkins:

```
Developer Commit
      ↓
git push origin feature-login
      ↓
Pull Request
      ↓
Merge to main
      ↓
CI Pipeline Trigger
      ↓
Build
      ↓
Test
      ↓
Docker Image Build
      ↓
Deployment
```

Often deployed to platforms like:

* Docker
* Kubernetes
* Amazon Web Services

---

✅ **Important Interview Tip**

Most DevOps interviews test **3 Git skills**:

1. **Branching strategy**
2. **Rollback strategy**
3. **CI/CD integration with Git**

---

If you want, I can also give you a **complete “Git for DevOps Engineer Roadmap (Beginner → Advanced → Expert)”**, which includes:

* Git branching strategies used in big companies
* GitFlow vs Trunk-based development
* How CI/CD tools integrate with Git
* Git architecture deep dive

This roadmap is extremely useful if you want to become a **DevOps Engineer in 3–6 months.**
