---

# Git Repository Basics

## What is a Git Repository

A **Git repository** is a directory where Git tracks all project files, history, commits, and branches.

It contains:

* project files
* commit history
* configuration files
* `.git` directory

The `.git` folder stores **all Git metadata** like commits, branches, logs, etc.

### Interview Definition

> A Git repository is a storage location where Git tracks project files, versions, commits, and history.

---

# 1. Create Repository

A repository can be created in two ways:

1. Initialize a new repository
2. Clone an existing repository

---

# git init

`git init` creates a **new Git repository in the current directory**.

### Syntax

```bash
git init
```

### Example

```bash
mkdir project
cd project
git init
```

Output

```
Initialized empty Git repository
```

This command creates a hidden folder:

```
.git
```

### What `.git` Contains

* commits
* branches
* configuration
* logs

### Interview Explanation

> The git init command initializes a new Git repository and creates the hidden .git directory that stores all version control information.

---

# 2. Clone Repository

`git clone` copies an **existing remote repository** to your local machine.

### Syntax

```bash
git clone <repository-url>
```

Example hosting platforms:

* GitHub
* GitLab
* Bitbucket

### Example

```bash
git clone https://github.com/user/project.git
```

### What Happens When You Clone

Git downloads:

* project files
* commit history
* branches
* configuration

### Interview Explanation

> git clone is used to copy an existing remote repository along with its entire history to the local machine.

---

# Git File Lifecycle

Every file in Git goes through **four states**.

```
Untracked → Modified → Staged → Committed
```

These states describe **how Git tracks file changes**.

---

# 1. Untracked

Files that **exist in the working directory but are not tracked by Git**.

Example:

```
newfile.txt
```

Git does not monitor these files yet.

### To track the file

```bash
git add newfile.txt
```

---

# 2. Modified

A file that **has been changed but not yet staged**.

Example

```
file.txt modified
```

Git detects the change but it is not ready for commit.

---

# 3. Staged

Files that are **prepared for commit**.

Added using:

```bash
git add filename
```

or

```bash
git add .
```

The staging area acts as a **pre-commit checkpoint**.

---

# 4. Committed

When staged files are saved permanently in the repository.

Command:

```bash
git commit -m "commit message"
```

Now Git records the snapshot.

---

# Git File Lifecycle Diagram

```
Working Directory
       │
       │ git add
       ↓
Staging Area
       │
       │ git commit
       ↓
Git Repository
```

---

# Checking Repository Status

## git status

`git status` shows the **current state of the repository**.

### Syntax

```bash
git status
```

### Example Output

```
On branch main
Untracked files:
   file1.txt

Changes not staged for commit:
   modified: file2.txt
```

### What git status Shows

* current branch
* untracked files
* modified files
* staged files
* commit status

### Interview Explanation

> git status displays the current state of the working directory and staging area, showing which files are modified, staged, or untracked.

---

# DevOps Interview Tip

Common Git workflow used in DevOps:

```
git init
git add .
git commit -m "message"
git push
```

or when working with remote repository:

```
git clone
git add
git commit
git push
git pull
```

---