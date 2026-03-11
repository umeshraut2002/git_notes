
---

# 1. Git Rebase vs Merge (Real Production Scenario)

## Git Merge

**Merge** combines changes from one branch into another and creates a **merge commit**.

### Command

```bash
git checkout main
git merge feature-login
```

### History

```
A---B---C main
     \  
      D---E feature
           \
            M (merge commit)
```

### Characteristics

* Preserves full commit history
* Shows branch structure
* Safe for shared branches

### Production Scenario

In a team working on a microservice repository hosted on GitHub:

1. Developer creates a feature branch.
2. Several developers commit changes.
3. Pull request is created.
4. Team merges using **merge commit**.

Used when:

* Many developers collaborate
* Audit trail is important
* CI/CD pipelines are triggered

Tools used with merge workflows:

* Jenkins
* GitHub Actions

---

## Git Rebase

Rebase **reapplies commits on top of another branch**, creating a **linear history**.

### Command

```bash
git checkout feature-login
git rebase main
```

### History

Before:

```
A---B---C main
     \
      D---E feature
```

After rebase:

```
A---B---C---D'---E'
```

### Characteristics

* Clean history
* No merge commits
* Rewrites commit history

### Production Scenario

A DevOps engineer working on infrastructure code:

* Terraform modules stored in Git
* Only one developer works on the branch

Before creating a PR, they run:

```bash
git rebase main
```

Result:

* Clean commit history
* Easier code review

### Interview Tip

Use:

**Merge → shared branches**

**Rebase → private feature branches**

---

# 2. Git Shallow Clone

## What is Shallow Clone?

A **shallow clone downloads only the latest commits instead of full history.**

This reduces **download time and disk usage**.

---

## Command

```bash
git clone --depth 1 repo-url
```

Example

```bash
git clone --depth 1 https://github.com/project/repo.git
```

---

## Why DevOps Engineers Use It

CI/CD pipelines often do **shallow clones**.

Example pipeline in GitHub Actions:

* Code checkout
* Build
* Test
* Deploy

Full Git history is **not needed**, so shallow clone speeds up pipeline.

---

## Benefits

* Faster cloning
* Less bandwidth
* Smaller repository size

---

# 3. Git Worktree

## What is Git Worktree?

Git worktree allows **multiple working directories for the same repository.**

You can work on **multiple branches simultaneously**.

---

## Command

Create new worktree

```bash
git worktree add ../feature-login feature-login
```

Now you have:

```
project-main/
project-feature-login/
```

Each directory represents a branch.

---

## Production Scenario

A DevOps engineer working on:

* production hotfix
* new feature

Instead of switching branches repeatedly:

```
hotfix branch → directory 1
feature branch → directory 2
```

Both run simultaneously.

---

## Benefits

* Parallel development
* Faster branch switching
* Better for debugging

---

# 4. Git Monorepo Strategy

## What is Monorepo?

A **monorepo (monolithic repository)** stores multiple projects in a single Git repository.

Example structure:

```
company-repo/
   frontend/
   backend/
   infrastructure/
   mobile/
```

---

## Companies Using Monorepo

Large companies like:

* Google
* Facebook
* Microsoft

---

## DevOps Benefits

1. Single source of truth
2. Easier dependency management
3. Unified CI/CD pipelines

Example pipeline:

```
Git Push
   ↓
CI Pipeline
   ↓
Detect changed folder
   ↓
Build only affected service
```

---

## Tools Used with Monorepo

* Bazel
* Nx
* Turborepo

---

# 5. Git Large File Storage (LFS)

## What is Git LFS?

Git LFS manages **large files like videos, datasets, and binaries**.

Instead of storing files in Git directly, it stores **references**.

---

## Problem Without LFS

Git repositories become huge when storing:

* datasets
* machine learning models
* binaries

---

## Install Git LFS

```bash
git lfs install
```

Track large files

```bash
git lfs track "*.zip"
```

Commit changes

```bash
git add .gitattributes
git commit -m "Enable LFS"
```

---

## DevOps Use Case

Used when repository contains:

* ML models
* Docker images
* datasets

Platforms supporting LFS:

* GitHub
* GitLab

---

# 6. Git Garbage Collection (git gc)

## What is Git GC?

Git GC (Garbage Collection) cleans unnecessary files and optimizes the repository.

Git stores objects in `.git/objects`.

Over time repository accumulates:

* dangling commits
* unused objects
* old blobs

---

## Command

```bash
git gc
```

---

## What It Does

1. Compress objects
2. Remove unreachable objects
3. Optimize repository storage

---

## Example Workflow

Developer deletes branches:

```
feature-login
feature-payment
```

Their commits still exist internally.

Running:

```bash
git gc
```

removes unused objects.

---

## DevOps Production Use Case

Large repositories running CI/CD may become slow.

Running **git gc** helps:

* reduce repo size
* improve Git performance
* optimize cloning speed

---

# Important Interview Summary

| Topic         | Purpose                          |
| ------------- | -------------------------------- |
| Rebase        | Clean commit history             |
| Merge         | Safe branch integration          |
| Shallow Clone | Faster CI/CD cloning             |
| Worktree      | Multiple branches simultaneously |
| Monorepo      | Multiple projects in one repo    |
| Git LFS       | Manage large files               |
| Git GC        | Optimize repository storage      |

---