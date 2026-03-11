

---

# Git 

## 1. What is Git?

**Answer**

Git is a **distributed version control system (DVCS)** used to track changes in source code during software development.

It allows multiple developers to work on the same project simultaneously while maintaining the history of changes.

**Key Features**

* Distributed architecture
* Branching and merging
* Version history tracking
* Collaboration support
* Fast performance

**Example**

```bash
git init
```

Creates a new Git repository.

---

# 2. Difference Between Git and GitHub

**Answer**

| Git                  | GitHub                  |
| -------------------- | ----------------------- |
| Version control tool | Cloud hosting platform  |
| Installed locally    | Hosted online           |
| Tracks code changes  | Stores Git repositories |
| CLI based            | Web interface           |

Example:

```bash
git push origin main
```

Pushes code from local Git to GitHub.

---

# 3. What is a Repository?

A **repository (repo)** is a storage location where the project files and their version history are stored.

Types:

* **Local repository**
* **Remote repository**

Example

```bash
git clone https://github.com/user/project.git
```

---

# 4. What is Git Clone?

**git clone** copies an existing repository from a remote server to your local machine.

Example

```bash
git clone https://github.com/project.git
```

Creates a complete local copy.

---

# 5. What is Git Pull?

**git pull** fetches changes from a remote repository and merges them into the local branch.

Example

```bash
git pull origin main
```

Steps internally:

1. git fetch
2. git merge

---

# 6. What is Git Push?

**git push** uploads local commits to a remote repository.

Example

```bash
git push origin main
```

---

# 7. What is Git Fetch?

**git fetch** downloads updates from a remote repository but does not merge them.

Example

```bash
git fetch origin
```

Difference:

| Fetch            | Pull             |
| ---------------- | ---------------- |
| Download changes | Download + Merge |

---

# 8. What is Git Branch?

A **branch** is an independent line of development.

It allows developers to work on features without affecting the main code.

Example

```bash
git branch feature-login
```

Create new branch.

Switch branch

```bash
git checkout feature-login
```

---

# 9. What is Git Merge?

Git merge combines changes from one branch into another.

Example

```bash
git merge feature-login
```

---

# 10. What is Git Rebase?

Rebase moves or reapplies commits on top of another base branch.

Example

```bash
git rebase main
```

Advantage:

* Cleaner commit history

---

# 11. Difference Between Merge and Rebase

| Merge                    | Rebase                    |
| ------------------------ | ------------------------- |
| Keeps history            | Rewrites history          |
| Creates merge commit     | Linear history            |
| Safe for shared branches | Used for private branches |

---

# 12. What is Git Stash?

Git stash temporarily saves uncommitted changes.

Example

```bash
git stash
```

Restore

```bash
git stash pop
```

Use case:

Developer switches branch without committing changes.

---

# 13. What is .gitignore?

`.gitignore` file specifies files Git should ignore.

Example

```
node_modules/
.env
logs/
```

Used to avoid committing:

* passwords
* logs
* dependencies

---

# 14. What is Git Tag?

Tags mark specific points in history (usually releases).

Example

```bash
git tag v1.0
```

Push tag

```bash
git push origin v1.0
```

---

# 15. What is Git Reset?

Git reset removes commits from history.

Types:

| Command | Meaning                  |
| ------- | ------------------------ |
| soft    | keep changes staged      |
| mixed   | keep changes but unstage |
| hard    | delete changes           |

Example

```bash
git reset --hard HEAD~1
```

Deletes last commit.

---

# 16. What is Git Revert?

Revert creates a new commit that undoes a previous commit.

Example

```bash
git revert commit-id
```

Safe for shared repositories.

---

# 17. What is Git Cherry Pick?

Cherry-pick applies a specific commit from one branch to another.

Example

```bash
git cherry-pick commit-id
```

---

# 18. What is Git HEAD?

HEAD is a pointer to the **current commit**.

Example

```bash
HEAD -> main -> commit
```

---

# 19. What is Git Workflow in DevOps?

Typical workflow:

1. Developer clones repo
2. Creates feature branch
3. Commit changes
4. Push to remote
5. Create Pull Request
6. Code review
7. Merge to main
8. CI/CD pipeline triggers

Tools used:

* Git
* GitHub
* GitLab
* Jenkins
* GitHub Actions

---

# 20. What is Git Used for in DevOps?

Git is used for:

* Source code versioning
* Infrastructure as Code
* CI/CD pipelines
* Configuration management
* Deployment automation

Example:

* Dockerfiles stored in Git
* Kubernetes YAML stored in Git
* CI/CD pipelines triggered from Git commits

---

# 21. What is Pull Request (PR)?

A Pull Request is a request to merge code from one branch to another.

Process:

1. Push branch
2. Create PR
3. Code review
4. Approval
5. Merge

Common in:

* GitHub
* GitLab
* Bitbucket

---

# 22. Git Architecture

Git has three main areas:

### 1 Working Directory

Project files you edit.

### 2 Staging Area

Prepared files before commit.

Command

```bash
git add file.txt
```

### 3 Repository

Permanent storage.

Command

```bash
git commit -m "update file"
```

---

# 23. Git File Lifecycle

```
Working Directory
        ↓
Staging Area
        ↓
Local Repository
        ↓
Remote Repository
```

Commands

```
git add
git commit
git push
```

---

# 24. How Git Helps CI/CD

Git triggers pipelines when code changes.

Example pipeline:

```
Developer Push Code
        ↓
GitHub Webhook
        ↓
CI/CD Tool Trigger
        ↓
Build
        ↓
Test
        ↓
Deploy
```

Used with:

* Docker
* Kubernetes
* Jenkins

---

# 25. Real DevOps Git Commands Used Daily

```
git clone
git pull
git add .
git commit -m "message"
git push
git branch
git checkout
git merge
git stash
git log
```
---

# 26. Git Squash

## What is Git Squash?

**Git squash** combines multiple commits into a **single commit**.

It is mainly used to **clean commit history before merging a feature branch**.

### Why DevOps teams use it

* Keeps repository history clean
* Removes unnecessary intermediate commits
* Makes code review easier

---

## Example

Suppose commits are:

```
Commit 1 → added login page
Commit 2 → fixed CSS
Commit 3 → fixed typo
```

Using squash → becomes

```
Single commit → Added login feature
```

---

## Command

```bash
git rebase -i HEAD~3
```

Then change:

```
pick
pick
pick
```

to

```
pick
squash
squash
```

---

# 27. Git Bisect

## What is Git Bisect?

**Git bisect** helps find the commit that introduced a bug using **binary search**.

Instead of checking every commit, Git automatically checks the middle commit.

---

## Example Scenario

Application was working in **commit A**
Bug appears in **commit Z**

Git bisect finds the **exact commit where the bug started**.

---

## Command Flow

Start bisect

```bash
git bisect start
```

Mark bad commit

```bash
git bisect bad
```

Mark good commit

```bash
git bisect good <commit-id>
```

Git will checkout middle commits automatically.

Mark results

```
git bisect good
git bisect bad
```

Finish

```
git bisect reset
```

---

## DevOps Use Case

Used when:

* CI/CD pipeline suddenly fails
* Production bug appears
* Need to locate problematic commit quickly

---

# 28. Git Reflog

## What is Git Reflog?

**Reflog records every change made to HEAD** in the repository.

Even if commits are deleted, reflog can **recover them**.

---

## Example

Developer accidentally deletes commits:

```
git reset --hard
```

But reflog still tracks them.

---

## Command

```bash
git reflog
```

Output example

```
abc123 HEAD@{0}: reset: moving to HEAD~1
def456 HEAD@{1}: commit: added feature
```

Recover commit

```bash
git checkout def456
```

---

## DevOps Use Case

Used for:

* Recovering lost commits
* Undoing mistakes
* Debugging repository history

---

# 29. Git Hooks

## What are Git Hooks?

**Git hooks are scripts that run automatically when specific Git events occur.**

They are stored in:

```
.git/hooks
```

---

## Types of Hooks

### Client-side hooks

Run on developer machine.

Examples

| Hook       | Trigger              |
| ---------- | -------------------- |
| pre-commit | before commit        |
| commit-msg | check commit message |
| pre-push   | before push          |

---

### Server-side hooks

Run on Git server.

Examples

| Hook         | Purpose          |
| ------------ | ---------------- |
| pre-receive  | validate commits |
| post-receive | trigger CI/CD    |

---

## Example

Pre-commit hook to check code formatting.

```
.git/hooks/pre-commit
```

Example script

```bash
#!/bin/sh
npm run lint
```

---

## DevOps Use Case

Used to:

* enforce coding standards
* run tests
* trigger CI pipelines

Tools often used with hooks:

* Jenkins
* GitHub Actions
* GitLab

---

# 30. Git Submodules

## What are Git Submodules?

A **submodule is a Git repository inside another Git repository**.

It allows one project to include another repository as a dependency.

---

## Example

Main project:

```
web-app
```

Submodule:

```
shared-library
```

---

## Add Submodule

```bash
git submodule add https://github.com/library.git
```

---

## Clone Project with Submodules

```bash
git clone --recurse-submodules repo-url
```

---

## DevOps Use Case

Used when:

* shared libraries
* infrastructure modules
* microservices dependencies

---

# 31. Git Patch Workflow

## What is Patch Workflow?

A **patch is a file containing the differences between commits**.

It allows developers to **share changes without direct repository access**.

---

## Create Patch

```bash
git format-patch HEAD~1
```

This creates:

```
0001-feature-update.patch
```

---

## Apply Patch

```bash
git apply file.patch
```

Or

```bash
git am file.patch
```

---

## DevOps Use Case

Used in:

* open-source projects
* email-based collaboration
* restricted repository access

Example: Linux kernel development.

---

# 32. Git Internals (Objects, Blobs, Trees)

Git internally stores everything as **objects**.

There are **three main Git objects**.

---

# 1 Blob (Binary Large Object)

Blob stores **file content**.

Example

```
file.txt → blob object
```

Blob does not store filename.

---

# 2 Tree

Tree represents a **directory structure**.

It contains:

* file names
* references to blobs

Example

```
project/
   app.js
   index.html
```

Stored as a **tree object**.

---

# 3 Commit Object

Commit contains:

* tree reference
* parent commit
* author
* timestamp
* commit message

---

## Git Object Model

```
Commit
  ↓
Tree
  ↓
Blob
```

---

## Example Commands

Show object

```bash
git cat-file -p <object-id>
```

List objects

```bash
git ls-tree HEAD
```

---

# How Git Stores Data

Git uses **SHA-1 hash** to store objects.

Example:

```
e4d909c290d0fb1ca068ffaddf22cbd0
```

Each commit gets a unique hash.

---

# Real DevOps Importance

Understanding Git internals helps when:

* debugging repository corruption
* recovering commits
* optimizing CI pipelines
* working with large repositories

---

✅ If you want, I can also show **10 extremely advanced Git interview questions that even senior DevOps engineers struggle with**, such as:

* **git rebase vs merge real production scenario**
* **git shallow clone**
* **git worktree**
* **git monorepo strategy**
* **git large file storage (LFS)**
* **git garbage collection (git gc)**

These are **very commonly asked in senior DevOps interviews.**
