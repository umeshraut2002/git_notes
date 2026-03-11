---

# 1. Version Control Fundamentals

## What is Version Control System (VCS)

A **Version Control System (VCS)** is a tool used to **track changes in source code over time** so developers can collaborate and maintain different versions of a project.

### Simple Interview Definition

> A Version Control System is a software tool that helps developers track changes in code, collaborate with teams, and maintain version history.

### Key Features

* Tracks code changes
* Maintains history
* Enables collaboration
* Allows rollback to previous versions

---

# Why VCS is Required in DevOps

In DevOps, **continuous development and deployment** require efficient code management.

### Reasons VCS is important

1. **Team collaboration**
   Multiple developers can work on the same project.

2. **Code history tracking**
   Every change is recorded.

3. **Rollback capability**
   If a bug occurs, we can revert to a stable version.

4. **CI/CD integration**
   DevOps pipelines trigger builds when code changes.

5. **Branching support**
   Developers can work on features independently.

### Interview Answer

> Version control is essential in DevOps because it enables collaboration, tracks code changes, supports branching strategies, and integrates with CI/CD pipelines.

---

# Types of Version Control Systems

There are **two main types of VCS**.

```
Version Control Systems
       │
       ├── Centralized VCS
       │
       └── Distributed VCS
```

---

# Centralized Version Control System (CVCS)

In CVCS, there is **one central server** that stores the repository, and all developers connect to it.

### Example tools

* Apache Subversion
* CVS

### Architecture

```
Developer → Central Server → Repository
```

### Advantages

* Simple to manage
* Centralized control

### Disadvantages

* Single point of failure
* Requires internet connection

---

# Distributed Version Control System (DVCS)

In DVCS, every developer has a **complete copy of the repository**, including history.

### Example tools

* Git
* Mercurial

### Architecture

```
Developer Repository ↔ Remote Repository
```

### Advantages

* Works offline
* Faster operations
* No single point of failure

### Disadvantages

* Slightly complex for beginners

---

# Introduction to Git

Git is a **distributed version control system** used to track changes in source code and manage collaborative development.

Git was created by:

* Linus Torvalds

Originally developed for the **Linux kernel project**.

### Interview Answer

> Git is a distributed version control system used to track changes in source code and enable collaboration among developers.

---

# Advantages of Git

### 1. Distributed architecture

Every developer has a full copy of the repository.

### 2. Fast performance

Most operations are local.

### 3. Powerful branching

Git supports lightweight branches.

### 4. Data integrity

Git tracks data using SHA hashing.

### 5. Offline capability

Developers can work without internet.

---

# Git vs SVN

| Feature      | Git                  | SVN             |
| ------------ | -------------------- | --------------- |
| Type         | Distributed VCS      | Centralized VCS |
| Speed        | Faster               | Slower          |
| Offline work | Yes                  | No              |
| Branching    | Easy                 | Difficult       |
| Repository   | Local copy available | Only server     |

SVN example:

* Apache Subversion

Git hosting platforms:

* GitHub
* GitLab
* Bitbucket

### Interview Answer

> Git is distributed and faster with powerful branching, while SVN is centralized and depends on a central server.

---

# Git Architecture

Git architecture consists of **three main areas**.

```
Working Directory
       ↓
Staging Area
       ↓
Local Repository
       ↓
Remote Repository
```

### 1 Working Directory

The directory where developers modify files.

### 2 Staging Area

Temporary area where files are prepared before committing.

### 3 Local Repository

Stores committed project history.

### 4 Remote Repository

Central repository used for collaboration.

Example remote hosts:

* GitHub
* GitLab

---

# Git Workflow Overview

Basic Git workflow:

```
Developer
   │
   │ git add
   ↓
Staging Area
   │
   │ git commit
   ↓
Local Repository
   │
   │ git push
   ↓
Remote Repository
```

### Step-by-step workflow

1. Modify files
2. Add files to staging
3. Commit changes
4. Push to remote repository
5. Pull latest changes from remote

### Important Commands

```
git add
git commit
git push
git pull
```

---

# 2. Git Installation

## Installing Git on Windows

1. Go to the official Git website:

* Git

Download installer.

2. Run the installer.

3. Select default options.

4. Finish installation.

---

## Verify Installation

Open terminal or command prompt and run:

```bash
git --version
```

Example output

```
git version 2.42.0
```

---

# Configure Git (Important for Interviews)

After installation configure username and email.

```bash
git config --global user.name "YourName"
```

```bash
git config --global user.email "your@email.com"
```

Check configuration

```bash
git config --list
```

---
