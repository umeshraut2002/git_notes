
---

# 6. Git Merging

## What is Merge

A **merge** in Git is the process of **combining changes from one branch into another branch**.

It is commonly used to **integrate feature branches into the main branch**.

### Example

```text
main
   \
    feature-login
```

After merging:

```text
main -----------M
   \           /
    feature-login
```

### Interview Definition

> Git merge is used to combine the changes from one branch into another branch.

---

# Fast-Forward Merge

A **fast-forward merge** occurs when the target branch has **no new commits since the branch was created**.

Git simply **moves the branch pointer forward**.

### Example

Before merge

```text
main → A → B
             \
              C → D (feature)
```

After merge

```text
main → A → B → C → D
```

No new merge commit is created.

### Key Point

Fast-forward merge happens when **history is linear**.

### Interview Explanation

> A fast-forward merge happens when the main branch has no new commits and Git simply moves the pointer forward to include the new commits.

---

# Three-Way Merge

A **three-way merge** occurs when both branches have **different commits**.

Git creates a **new merge commit**.

### Example

Before merge

```text
      C
     /
A → B
     \
      D
```

After merge

```text
      C
     / \
A → B   M
     \ /
      D
```

`M` = merge commit

### Interview Explanation

> A three-way merge occurs when two branches diverge and Git creates a new merge commit to combine the histories.

---

# Merge Conflicts

A **merge conflict** happens when **two branches modify the same line in a file**.

Git cannot automatically decide which change to keep.

### Example Conflict

```text
<<<<<<< HEAD
console.log("Version A");
=======
console.log("Version B");
>>>>>>> feature
```

The developer must choose the correct code.

### Interview Explanation

> Merge conflicts occur when Git cannot automatically merge changes because the same part of a file was modified in different branches.

---

# Resolve Merge Conflicts

Steps to resolve conflicts:

1. Open the conflicted file
2. Edit the code manually
3. Remove conflict markers
4. Add the file again
5. Commit the merge

### Commands

```bash
git add filename
git commit
```

---

# Important Merge Commands

## git merge

Used to merge one branch into the current branch.

### Syntax

```bash
git merge <branch-name>
```

Example

```bash
git merge feature-login
```

### Interview Explanation

> git merge integrates changes from another branch into the current branch.

---

## git mergetool

Used to resolve merge conflicts using a **visual merge tool**.

### Syntax

```bash
git mergetool
```

This opens a **GUI merge editor**.

### Interview Explanation

> git mergetool launches a visual tool to help resolve merge conflicts.

---

# 7. Remote Repository

A **remote repository** is a Git repository hosted on a server for team collaboration.

Popular platforms include:

* GitHub
* GitLab
* Bitbucket

---

# Local vs Remote Repository

| Feature  | Local Repository  | Remote Repository  |
| -------- | ----------------- | ------------------ |
| Location | Developer machine | Server             |
| Access   | Private           | Team collaboration |
| Usage    | Development       | Sharing code       |

### Interview Explanation

> A local repository exists on the developer's machine, while a remote repository is hosted on a server for collaboration.

---

# Add Remote Repository

## git remote add origin

Used to connect a local repository to a remote repository.

### Syntax

```bash
git remote add origin <repository-url>
```

Example

```bash
git remote add origin https://github.com/user/project.git
```

Check remote:

```bash
git remote -v
```

### Interview Explanation

> git remote add origin links a local Git repository to a remote repository.

---

# Push Code

## git push

Push sends **local commits to the remote repository**.

### Syntax

```bash
git push origin main
```

Example

```bash
git push origin main
```

### Interview Explanation

> git push uploads local commits to the remote repository.

---

# Pull Code

## git pull

Pull **downloads changes and automatically merges them**.

### Syntax

```bash
git pull origin main
```

### What it does internally

```text
git fetch + git merge
```

### Interview Explanation

> git pull fetches the latest changes from the remote repository and merges them into the current branch.

---

# Fetch Code

## git fetch

Fetch **downloads changes from the remote repository but does not merge them**.

### Syntax

```bash
git fetch
```

### Interview Explanation

> git fetch retrieves the latest changes from the remote repository without merging them.

---

# Interview Question

## Difference Between git pull and git fetch

| Feature             | git fetch    | git pull            |
| ------------------- | ------------ | ------------------- |
| Download changes    | Yes          | Yes                 |
| Merge automatically | No           | Yes                 |
| Safe operation      | Yes          | Can cause conflicts |
| Control             | More control | Less control        |

### Example

```bash
git fetch
git merge origin/main
```

vs

```bash
git pull
```

### Best Practice in DevOps

DevOps engineers often prefer:

```bash
git fetch
```

because it allows **reviewing changes before merging**