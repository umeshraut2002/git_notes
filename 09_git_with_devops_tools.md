## 16. Git in DevOps CI/CD Pipeline

In **modern DevOps**, Git acts as the **single source of truth for code**.
When developers push code to a repository, it **automatically triggers CI/CD pipelines** that build, test, and deploy the application.

Typical DevOps flow:

```
Developer → Git Commit
        ↓
Push to Git repository
        ↓
CI/CD Pipeline Trigger
        ↓
Build + Test
        ↓
Deploy to Server / Cloud
```

---

# How Git Integrates with DevOps Tools

Git repositories integrate with CI/CD platforms such as:

* Jenkins
* GitHub (via **GitHub Actions**)
* GitLab (via **GitLab CI/CD**)
* Azure DevOps

These tools **listen to Git events** like:

* push
* pull request
* merge

When such events happen, the **pipeline automatically runs**.

---

# Basic DevOps Workflow Using Git

### Step 1 — Developer Writes Code

A developer writes code and commits it.

```
git add .
git commit -m "Added login feature"
```

---

### Step 2 — Push Code to Remote Repository

```
git push origin main
```

The code is pushed to a remote repository such as **GitHub or GitLab**.

---

### Step 3 — CI/CD Pipeline Trigger

When the push happens, the CI/CD tool detects the change and **triggers the pipeline automatically**.

Example triggers:

* push to main branch
* pull request created
* tag created

---

### Step 4 — Build Stage

The pipeline builds the application.

Example tasks:

* compile code
* install dependencies
* create build artifacts

Example:

```
npm install
npm build
```

---

### Step 5 — Test Stage

Automated tests run to ensure the code works correctly.

Examples:

* unit tests
* integration tests
* security scans

Example:

```
npm test
```

---

### Step 6 — Deployment Stage

If all tests pass, the application is deployed to:

* development server
* staging environment
* production environment

Deployment targets may include:

* cloud servers
* containers
* Kubernetes clusters

---

# Real DevOps CI/CD Pipeline Flow

```
Developer
   ↓
git commit
   ↓
git push
   ↓
Git repository (GitHub/GitLab)
   ↓
CI/CD tool triggers pipeline
   ↓
Build stage
   ↓
Test stage
   ↓
Artifact creation
   ↓
Deploy to server/cloud
```

---

# Example: Git + Jenkins Pipeline

Flow using **Jenkins**:

```
Developer pushes code to GitHub
        ↓
Webhook triggers Jenkins
        ↓
Jenkins pipeline starts
        ↓
Build application
        ↓
Run tests
        ↓
Deploy to server
```

---

# Example: GitHub Actions CI/CD

With **GitHub Actions**, workflows are defined inside the repository.

Example pipeline file:

```
.github/workflows/build.yml
```

Example structure:

```yaml
name: CI Pipeline

on: push

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm install
      - run: npm test
```

When code is pushed → pipeline automatically runs.

---

# Why Git Is Critical in DevOps

| Reason                 | Explanation                     |
| ---------------------- | ------------------------------- |
| Single source of truth | All code versions stored in Git |
| Automation trigger     | Push events trigger pipelines   |
| Collaboration          | Multiple developers work safely |
| Traceability           | Every change is tracked         |

---

# Interview Example Explanation

**Question:** How does Git integrate with CI/CD?

**Answer:**

> In DevOps, Git acts as the source code repository. When developers push code to Git platforms like GitHub or GitLab, it triggers CI/CD pipelines in tools like Jenkins or GitHub Actions. The pipeline then automatically builds the application, runs tests, and deploys the application to the target environment.

---

# 10-Second Interview Answer

> Git integrates with CI/CD pipelines by triggering automated workflows whenever code is pushed or merged. CI/CD tools like Jenkins, GitHub Actions, GitLab CI/CD, and Azure DevOps use these triggers to build, test, and deploy applications automatically.

---

---

Below are **clear, interview-focused explanations** for these three Git concepts. These are very commonly asked in **DevOps / Git interviews**, so I’ll keep them **simple + technically accurate**.

---

# 1. What Happens Internally When You Run `git push`

`git push` sends your **local commits to a remote repository**.

Example:

```bash
git push origin main
```

### Internal Steps

1️⃣ **Local Git checks commits**
Git checks the commits in your local branch that **do not exist on the remote branch**.

2️⃣ **Connects to the remote repository**
Git connects to the remote server (for example a repo on GitHub, GitLab, or Bitbucket).

3️⃣ **Authentication happens**
Git verifies:

* SSH key
  or
* username + token

4️⃣ **Transfers missing commits**

Git sends:

* commits
* blobs (file data)
* trees (directory structure)

5️⃣ **Remote branch gets updated**

The remote branch pointer moves forward to the **latest commit**.

---

### Visual Flow

```
Local Repository
   |
   | git push
   v
Remote Repository
(origin/main updated)
```

---

### Simple Interview Answer

> When `git push` is executed, Git identifies commits in the local branch that do not exist in the remote branch. It then connects to the remote repository, transfers those commits and objects, and updates the remote branch reference.

---

# 2. Difference Between `git fetch`, `git pull`, and `git clone`

These commands deal with **getting code from a remote repository**.

---

## `git clone`

**Purpose:**
Download a repository for the **first time**.

Example:

```bash
git clone https://github.com/project/repo.git
```

### What it does internally

1. Creates a new folder
2. Downloads the entire repository
3. Creates a remote called **origin**
4. Checks out the default branch

---

### Visual

```
Remote Repo
   |
git clone
   v
Local Repo created
```

---

## `git fetch`

**Purpose:**
Download changes from the remote repository **without merging them**.

Example:

```bash
git fetch origin
```

### What happens

* Downloads new commits
* Updates remote tracking branch
* Does NOT modify your working code

Example:

```
origin/main updated
local main unchanged
```

---

### Visual

```
Remote Repo
   |
git fetch
   v
Local repo updated (no merge)
```

---

## `git pull`

**Purpose:**
Download changes **and merge them automatically**.

Example:

```bash
git pull origin main
```

### Internally it runs

```
git fetch
+
git merge
```

So your branch immediately gets updated.

---

### Visual

```
Remote Repo
   |
git pull
   v
Fetch + Merge
   v
Local branch updated
```

---

### Comparison Table

| Command   | Purpose                  | Changes Local Code |
| --------- | ------------------------ | ------------------ |
| git clone | Download repo first time | Yes                |
| git fetch | Download updates only    | No                 |
| git pull  | Download + merge updates | Yes                |

---

### Simple Interview Answer

> `git clone` copies a repository for the first time. `git fetch` downloads changes from the remote repository without modifying the working directory. `git pull` downloads changes and automatically merges them into the current branch.

---

# 3. What is HEAD in Git

**HEAD is a pointer to the current commit you are working on.**

It usually points to the **latest commit of the current branch**.

---

### Example

```
main branch
   |
   v
commit1 → commit2 → commit3
                      ↑
                     HEAD
```

HEAD means:

> “This is the current working position in the repository.”

---

### Example Command

```
git checkout feature-login
```

Now HEAD moves to that branch.

```
feature-login
      |
      v
commitA → commitB
              ↑
             HEAD
```

---

### Detached HEAD

Sometimes HEAD points **directly to a commit**, not a branch.

Example:

```
git checkout a1b2c3
```

Now you are in **detached HEAD state**.

---

### Simple Interview Answer

> HEAD is a pointer that refers to the current commit or branch that Git is currently working on. It usually points to the latest commit in the active branch.

---

# Quick 30-Second Interview Summary

**git push**

* Sends local commits to remote repository.

**git clone**

* Copies a repository for the first time.

**git fetch**

* Downloads updates but does not merge.

**git pull**

* Fetch + merge updates.

**HEAD**

* Pointer to the current commit or branch you are working on.

---

Below are **important Git interview questions explained simply**. These are frequently asked in **DevOps interviews**, so focus on the **concept + practical scenario**.

---

# 1. `git merge` vs `git rebase`

Both are used to **integrate changes from one branch into another**, but they work differently.

## git merge

**Merge combines two branches and creates a new merge commit.**

Example:

```bash
git checkout main
git merge feature
```

### History with Merge

```text
A---B---C main
     \   
      D---E feature
           \
            M (merge commit)
```

A **merge commit (M)** is created.

### Characteristics

* Keeps **complete branch history**
* Safer for teams
* Default method in most projects

---

## git rebase

**Rebase moves (replays) commits from one branch onto another branch.**

Example:

```bash
git checkout feature
git rebase main
```

### History with Rebase

```text
A---B---C main
         \
          D'---E' feature
```

Commits are **rewritten** and appear after `main`.

### Characteristics

* Cleaner linear history
* No merge commit
* Rewrites history

---

### Key Difference

| Feature | Merge                    | Rebase                   |
| ------- | ------------------------ | ------------------------ |
| History | Preserved                | Rewritten                |
| Commit  | Creates merge commit     | No merge commit          |
| Safety  | Safe for shared branches | Risky on shared branches |

---

### Interview Answer

> `git merge` combines branches and creates a merge commit, preserving history. `git rebase` moves commits to another base commit, creating a cleaner linear history but rewriting commit history.

---

# 2. `origin` vs `upstream`

These terms refer to **remote repositories**.

## origin

`origin` is the **default remote repository** created when you clone a repo.

Example:

```bash
git clone https://github.com/project/repo.git
```

Git automatically sets:

```bash
origin → remote repository
```

Example:

```bash
git push origin main
```

---

## upstream

`upstream` refers to the **original repository you forked from**.

Common when contributing to open-source projects on GitHub.

Example setup:

```bash
git remote add upstream https://github.com/original/repo.git
```

Now you have:

```text
origin   → your fork
upstream → original repository
```

---

### Example Workflow

```bash
git fetch upstream
git merge upstream/main
```

This pulls updates from the original project.

---

### Interview Answer

> `origin` is the default remote repository created when cloning a repo. `upstream` refers to the original repository from which a fork was created, usually used to sync updates.

---

# 3. `fork` vs `clone`

These are often confused.

## fork

A **fork creates a copy of a repository on your Git hosting platform**.

Example on GitHub:

```text
Original Repo → Fork → Your GitHub account
```

Used for:

* contributing to open-source
* making independent changes

---

## clone

A **clone copies the repository from remote to your local machine**.

Example:

```bash
git clone https://github.com/user/repo.git
```

Result:

```text
Remote Repo → Local Machine
```

---

### Key Difference

| Feature  | Fork                  | Clone             |
| -------- | --------------------- | ----------------- |
| Location | Server copy           | Local copy        |
| Purpose  | Contribution workflow | Local development |

---

### Interview Answer

> Fork creates a server-side copy of a repository on platforms like GitHub. Clone downloads a repository from a remote server to the local machine.

---

# 4. `git stash` vs `git commit`

Both save changes but serve different purposes.

---

## git commit

A **commit permanently saves changes in repository history**.

Example:

```bash
git add .
git commit -m "Added login feature"
```

Commit becomes part of the project history.

---

## git stash

`git stash` **temporarily saves uncommitted changes**.

Example:

```bash
git stash
```

Your working directory becomes clean.

Later you restore changes:

```bash
git stash apply
```

---

### Example Scenario

You are coding but need to switch branches.

Instead of committing incomplete work:

```bash
git stash
git checkout main
```

---

### Difference

| Feature        | Commit             | Stash                 |
| -------------- | ------------------ | --------------------- |
| Storage        | Permanent history  | Temporary storage     |
| Visible in log | Yes                | No                    |
| Use case       | Save finished work | Pause unfinished work |

---

### Interview Answer

> A commit permanently records changes in the repository history, while stash temporarily saves uncommitted changes so you can switch branches or work on something else.

---

# 5. Why CI Pipelines Trigger on Push

In DevOps, CI pipelines are triggered when **new code is pushed to a repository**.

Example tools:

* Jenkins
* GitHub Actions
* GitLab CI/CD
* Azure DevOps

---

## How It Works

1️⃣ Developer pushes code

```bash
git push origin main
```

2️⃣ Git platform sends a **webhook event**

3️⃣ CI/CD tool receives the event

4️⃣ Pipeline starts automatically

---

### Pipeline Flow

```text
Developer
   ↓
git push
   ↓
Git Repository
   ↓
Webhook trigger
   ↓
CI/CD Pipeline
   ↓
Build → Test → Deploy
```

---

## Why This Is Important

Push triggers ensure:

* automated testing
* automated builds
* faster feedback
* continuous delivery

---

### Interview Answer

> CI pipelines trigger on push because Git platforms send webhook events whenever code is pushed. CI/CD tools listen to these events and automatically start the build, test, and deployment process.

---

# Quick DevOps Interview Summary

**Merge vs Rebase**

* Merge keeps history
* Rebase rewrites history

**Origin vs Upstream**

* origin → your repository
* upstream → original repository

**Fork vs Clone**

* Fork → server copy
* Clone → local copy

**Stash vs Commit**

* Commit → permanent
* Stash → temporary

**CI Trigger**

* Push event triggers automated pipeline.

---