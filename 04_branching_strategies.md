---

# 9. Git Branching Strategies (Important for DevOps)

Branching strategies define **how teams organize branches to develop, test, and release software efficiently**.

They help teams:

* collaborate safely
* maintain stable production code
* enable CI/CD pipelines
* release features faster

---

# 1. Git Flow

Git Flow is a **structured branching model** used for large projects with scheduled releases.

### Main Branches

| Branch        | Purpose                         |
| ------------- | ------------------------------- |
| main / master | Production-ready code           |
| develop       | Integration branch for features |

### Supporting Branches

* feature
* release
* hotfix

---

### Git Flow Structure

```text
main
  |
  |-------- hotfix
  |
develop
   |
   |--- feature-login
   |--- feature-payment
   |
   └--- release-v1.0
```

---

### Workflow

1. Developers create **feature branches** from develop.
2. Features merge back into **develop**.
3. A **release branch** prepares production release.
4. Code merges into **main**.

---

### Interview Answer

> Git Flow is a branching strategy where development happens in feature branches from the develop branch, and stable releases are merged into the main branch.

---

# 2. Feature Branch Workflow

In this workflow **each feature is developed in a separate branch**.

---

### Structure

```text
main
  |
  |--- feature-login
  |
  |--- feature-payment
```

---

### Workflow

1. Create feature branch

```bash
git checkout -b feature-login
```

2. Develop code
3. Push branch
4. Create pull request
5. Merge into main

---

### Benefits

* isolates feature development
* safer collaboration
* easy code review

---

### Interview Explanation

> Feature branch workflow allows developers to work on features in isolated branches and merge them into the main branch after review.

---

# 3. Trunk Based Development

This is a **modern DevOps practice used by companies practicing continuous delivery**.

All developers commit frequently to **one main branch (trunk)**.

---

### Structure

```text
main (trunk)
   |
   |--- small short-lived branches
```

Branches live for **a few hours or a day**.

---

### Key Rules

* small commits
* frequent integration
* automated CI/CD

---

### Companies using this model

Many large tech companies prefer trunk-based development.

---

### Interview Explanation

> Trunk-based development is a strategy where developers frequently commit small changes directly to the main branch or short-lived branches.

---

# 4. Release Branch

Release branches are used when preparing a **production release**.

---

### Example

```text
main
  |
develop
  |
  |--- release-v2.0
```

---

### Purpose

* bug fixes
* release testing
* final stabilization

---

### Workflow

1. Create release branch from develop

```bash
git checkout -b release-2.0
```

2. Fix bugs
3. Merge into main
4. Deploy

---

### Interview Explanation

> A release branch is created to prepare code for production by performing final testing and bug fixes before merging into the main branch.

---

# 5. Hotfix Branch

Hotfix branches are used to **fix urgent production issues**.

They branch from **main**.

---

### Example

```text
main
  |
  |--- hotfix-login-bug
```

---

### Workflow

1. Create hotfix branch

```bash
git checkout -b hotfix-login-bug
```

2. Fix production issue
3. Merge into main
4. Deploy immediately

---

### Interview Explanation

> A hotfix branch is used to quickly fix critical bugs in production without waiting for the next release cycle.

---

# DevOps Pipeline Using Branch Strategies

Typical DevOps CI/CD flow:

```text
Developer → Feature Branch → Pull Request
        ↓
   CI Pipeline (build + test)
        ↓
Merge to main
        ↓
CD Pipeline → Deployment
```

CI/CD tools often integrated with Git:

* Jenkins
* GitHub Actions
* GitLab CI/CD

---

# Comparison of Branching Strategies

| Strategy       | Best For                             |
| -------------- | ------------------------------------ |
| Git Flow       | Large projects with planned releases |
| Feature Branch | Team collaboration                   |
| Trunk Based    | Continuous delivery                  |
| Release Branch | Preparing production release         |
| Hotfix Branch  | Urgent production fixes              |

---

# Easy Way to Remember (Interview Trick)

```text
Feature  → develop new functionality
Release  → prepare production version
Hotfix   → fix urgent production bug
Trunk    → continuous integration
Git Flow → structured branching model
```

---
---