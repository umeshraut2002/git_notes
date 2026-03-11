
---

## What is Branching

A **branch** in Git is an **independent line of development** that allows developers to work on features, fixes, or experiments without affecting the main codebase.

Each branch contains its **own commits and history**.

### Example

```
main branch
     |
     |--- feature-login
     |
     |--- feature-payment
```

### Interview Definition

> A Git branch is an independent line of development that allows developers to work on new features without affecting the main codebase.

---

# Why Branching is Important in DevOps

Branching is very important in **DevOps and CI/CD workflows**.

### 1. Parallel development

Multiple developers can work on different features simultaneously.

### 2. Safe experimentation

New features can be tested without breaking the main application.

### 3. Code stability

Production code remains stable in the **main branch**.

### 4. CI/CD integration

DevOps pipelines trigger builds and tests when code is pushed to branches.

Example DevOps platforms using Git branching:

* GitHub
* GitLab
* Bitbucket

### Interview Answer

> Branching allows developers to work on multiple features simultaneously while keeping the main codebase stable, which is essential for DevOps and CI/CD workflows.

---

# Create Branch

## git branch

This command creates a **new branch**.

### Syntax

```bash
git branch <branch-name>
```

### Example

```bash
git branch feature-login
```

This creates a new branch but **does not switch to it**.

### Interview Explanation

> The git branch command is used to create a new branch in the repository.

---

# Switch Branch

## git checkout

Used to **switch from one branch to another**.

### Syntax

```bash
git checkout <branch-name>
```

### Example

```bash
git checkout feature-login
```

Now you are working in **feature-login branch**.

### Interview Explanation

> git checkout is used to switch between branches in a Git repository.

---

# Create and Switch Branch

## git checkout -b

This command **creates a branch and switches to it immediately**.

### Syntax

```bash
git checkout -b <branch-name>
```

### Example

```bash
git checkout -b feature-payment
```

Equivalent to:

```
git branch feature-payment
git checkout feature-payment
```

### Interview Explanation

> git checkout -b creates a new branch and switches to it in a single command.

---

# Delete Branch

Branches can be deleted when they are no longer needed.

### Syntax

```bash
git branch -d <branch-name>
```

### Example

```bash
git branch -d feature-login
```

Force delete:

```bash
git branch -D feature-login
```

### Interview Explanation

> git branch -d deletes a branch that has already been merged into the main branch.

---

# List Branches

To see all branches in the repository.

### Command

```bash
git branch
```

### Example Output

```
* main
  feature-login
  feature-payment
```

`*` indicates the **current active branch**.

### Interview Explanation

> git branch lists all branches in the repository and shows the current active branch.

---

# Branch Workflow in DevOps

Typical workflow:

```
main branch
      |
      | create feature branch
      ↓
feature branch
      |
      | develop code
      ↓
commit changes
      |
      | merge to main
      ↓
deployment pipeline
```

---

# Quick Branch Commands Cheat Sheet

| Command                | Purpose           |
| ---------------------- | ----------------- |
| git branch             | Create branch     |
| git branch -a          | List all branches |
| git checkout branch    | Switch branch     |
| git checkout -b branch | Create and switch |
| git branch -d branch   | Delete branch     |

---