---

# 10. Undoing Changes in Git

Sometimes developers need to **undo mistakes**, remove commits, or restore files.
Git provides several commands to undo changes safely.

Important commands:

```text
git reset
git revert
git checkout
git restore
```

---

# 1. git reset

`git reset` is used to **move the HEAD pointer to a previous commit**.

It can also modify the **staging area and working directory** depending on the reset type.

### Syntax

```bash
git reset <commit-id>
```

Example:

```bash
git reset HEAD~1
```

This removes the **latest commit**.

---

### Example

Before reset:

```text
A → B → C → D (HEAD)
```

Run:

```bash
git reset HEAD~1
```

After reset:

```text
A → B → C (HEAD)
```

Commit **D disappears**.

---

### Interview Explanation

> git reset moves the branch pointer to a previous commit and can remove commits from history.

---

# 2. git revert

`git revert` **undoes a commit by creating a new commit** that reverses the changes.

It **does not remove commit history**, so it is safer in shared repositories.

---

### Syntax

```bash
git revert <commit-id>
```

Example:

```bash
git revert HEAD
```

---

### Example

Before:

```text
A → B → C → D
```

After revert:

```text
A → B → C → D → E
```

`E` reverses changes made in `D`.

---

### Interview Explanation

> git revert creates a new commit that reverses the changes made in a previous commit without deleting the history.

---

# 3. git checkout

`git checkout` is used to **switch branches or restore files from a previous commit**.

---

### Switch branch

```bash
git checkout main
```

---

### Restore file

```bash
git checkout HEAD -- file.txt
```

This restores the file from the last commit.

---

### Interview Explanation

> git checkout is used to switch branches or restore files from a specific commit.

---

# 4. git restore

`git restore` is a newer command introduced to **restore working directory files**.

It is safer and more specific than checkout.

---

### Syntax

Restore file:

```bash
git restore file.txt
```

Restore staged file:

```bash
git restore --staged file.txt
```

---

### Interview Explanation

> git restore is used to discard changes in the working directory or unstage files.

---

# Interview Question 1

# Difference Between git reset and git revert

| Feature  | git reset            | git revert          |
| -------- | -------------------- | ------------------- |
| History  | Removes commits      | Keeps history       |
| Commits  | Deletes commits      | Creates new commit  |
| Safety   | Risky in shared repo | Safe in shared repo |
| Use case | Local undo           | Production rollback |

---

### Easy Way to Remember

```text
Reset  → delete commits
Revert → undo commits
```

---

### Interview Answer

> git reset moves the branch pointer to a previous commit and removes commits from history, while git revert creates a new commit that reverses previous changes without removing history.

---

# Interview Question 2

# Difference Between Soft / Mixed / Hard Reset

These are **three modes of git reset**.

---

## Soft Reset

Moves HEAD but **keeps changes staged**.

Command:

```bash
git reset --soft HEAD~1
```

Result:

| Area              | Status    |
| ----------------- | --------- |
| Working directory | unchanged |
| Staging area      | unchanged |
| Commit history    | removed   |

Use case: change commit message.

---

## Mixed Reset (Default)

Moves HEAD and **unstages files**.

Command:

```bash
git reset --mixed HEAD~1
```

Result:

| Area              | Status    |
| ----------------- | --------- |
| Working directory | unchanged |
| Staging area      | cleared   |
| Commit history    | removed   |

---

## Hard Reset

Moves HEAD and **deletes all changes**.

Command:

```bash
git reset --hard HEAD~1
```

Result:

| Area              | Status  |
| ----------------- | ------- |
| Working directory | deleted |
| Staging area      | deleted |
| Commit history    | removed |

---

# Visual Explanation

Before reset:

```text
Working Directory → Staging → Commit
```

After reset types:

| Reset Type | Working Dir | Staging | Commit |
| ---------- | ----------- | ------- | ------ |
| Soft       | keep        | keep    | remove |
| Mixed      | keep        | remove  | remove |
| Hard       | remove      | remove  | remove |

---

# DevOps Best Practice

DevOps engineers usually avoid:

```bash
git reset --hard
```

on **shared branches**.

Instead they prefer:

```bash
git revert
```

because it keeps history safe.

---

# 30-Second Interview Answer

You can say this:

> Git provides several commands to undo changes. git reset moves the branch pointer to a previous commit and can remove commits from history. git revert safely undoes changes by creating a new commit. git checkout is used to switch branches or restore files, and git restore is used to discard working directory changes. In git reset, soft reset keeps changes staged, mixed reset unstages files, and hard reset deletes all changes.

```