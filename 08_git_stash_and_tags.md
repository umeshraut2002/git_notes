
---

# Stash

## What is Git Stash

`git stash` is used to **temporarily save uncommitted changes without committing them**.

It allows you to **switch branches or pull updates without losing your current work**.

### Simple Definition (Interview)

> Git stash temporarily saves uncommitted changes and restores the working directory to the last committed state.

---

# Why Git Stash is Used

Common scenario in development.

### Example Scenario

You are working on a feature branch:

```text
feature-login
```

You modified files but **did not commit yet**.

Suddenly you must switch to **main branch to fix a bug**.

But Git will not allow switching because of uncommitted changes.

Solution:

```bash
git stash
```

This saves the changes temporarily.

---

# Save Temporary Changes

### Command

```bash
git stash
```

This will:

* save current changes
* clean the working directory

Example output:

```text
Saved working directory and index state
```

---

# Apply Stashed Changes

### Command

```bash
git stash apply
```

This restores the **latest stash**.

Example workflow:

```bash
git stash
git checkout main
fix bug
git checkout feature-login
git stash apply
```

Your changes return.

---

# List Stashes

You can store multiple stashes.

### Command

```bash
git stash list
```

Example output:

```text
stash@{0}: WIP on feature-login
stash@{1}: WIP on main
```

Each stash has an index number.

---

# Additional Useful Commands

Apply specific stash:

```bash
git stash apply stash@{1}
```

Delete stash:

```bash
git stash drop
```

Apply + remove stash:

```bash
git stash pop
```

---

# Interview Explanation

> Git stash temporarily stores uncommitted changes so developers can switch branches or pull updates without committing incomplete work.

---

# 12. Git Tags and Releases

## What are Tags

A **tag** is a reference to a specific commit, usually used to mark **release versions**.

Example versions:

```text
v1.0
v2.0
v3.1
```

Tags are commonly used when releasing software.

---

## Real DevOps Scenario

Example project release workflow:

```text
Development → Testing → Production
```

Once stable version is ready:

```bash
git tag v1.0
```

This marks the **release version**.

CI/CD pipelines can deploy based on tags.

Platforms like:

* GitHub
* GitLab
* Bitbucket

use tags for **release management**.

---

# Types of Git Tags

Two types exist.

---

# 1. Lightweight Tag

A lightweight tag is simply a **pointer to a commit**.

It contains **no additional metadata**.

### Command

```bash
git tag v1.0
```

---

# 2. Annotated Tag

Annotated tags contain additional information:

* tagger name
* email
* date
* message

Used for **official releases**.

### Command

```bash
git tag -a v1.0 -m "First release"
```

---

# View All Tags

```bash
git tag
```

Example:

```text
v1.0
v1.1
v2.0
```

---

# Push Tags to Remote Repository

Tags are not pushed automatically.

You must push them manually.

### Push single tag

```bash
git push origin v1.0
```

### Push all tags

```bash
git push origin --tags
```

---

# DevOps Release Workflow

Typical release process:

```text
Developer commits code
        ↓
Code tested
        ↓
Create release tag
        ↓
CI/CD pipeline triggers deployment
```

Example:

```bash
git tag -a v2.0 -m "Production release"
git push origin --tags
```

Pipeline triggers deployment.

---

# Difference Between Lightweight and Annotated Tag

| Feature        | Lightweight Tag | Annotated Tag       |
| -------------- | --------------- | ------------------- |
| Metadata       | No              | Yes                 |
| Release usage  | Rare            | Common              |
| Commit message | No              | Yes                 |
| Best for       | temporary marks | production releases |

---

# Easy Way to Remember

```text
Lightweight tag → simple pointer
Annotated tag → full release information
```

---

# 20-Second Interview Answer

You can say this confidently:

> Git stash temporarily saves uncommitted changes so developers can switch branches without committing incomplete work. Git tags are used to mark specific commits, usually for release versions. There are two types of tags: lightweight tags, which are simple pointers, and annotated tags, which store metadata like tag message and author. Tags can be pushed to remote repositories using git push origin --tags.

---
