


---

# 13. Git Rebase (Advanced)

## What is Rebase

`git rebase` is used to **move or reapply commits from one branch onto another branch**.

Instead of merging histories, rebase **creates a clean, linear commit history**.

### Simple Definition (Interview)

> Git rebase is used to move commits from one branch to another base commit to maintain a clean and linear project history.

---

## Example Scenario

You created a feature branch.

### Before Rebase

```text
main:     A → B → C
               \
feature:        D → E
```

Now run:

```bash
git checkout feature
git rebase main
```

### After Rebase

```text
main:     A → B → C → D → E
```

Git **moves commits D and E on top of C**.

---

## Why Rebase is Used

Rebase is mainly used to:

1. Keep commit history **clean**
2. Avoid unnecessary **merge commits**
3. Make project history **linear**
4. Improve **code readability**

---

# Merge vs Rebase

This is a **very common DevOps interview question**.

## Merge

Merge combines branches and **creates a merge commit**.

### Example

Before merge:

```text
main:     A → B → C
               \
feature:        D → E
```

Run:

```bash
git merge feature
```

After merge:

```text
main:     A → B → C → M
               \     /
feature:        D → E
```

`M` = merge commit

---

## Rebase

Rebase **moves commits to a new base commit**.

### Example

After rebase:

```text
main: A → B → C → D → E
```

No merge commit.

---

## Merge vs Rebase Table

| Feature      | Merge           | Rebase              |
| ------------ | --------------- | ------------------- |
| History      | Non-linear      | Linear              |
| Merge commit | Yes             | No                  |
| Safety       | Safe            | Can rewrite history |
| Usage        | Shared branches | Feature branches    |

---

## Easy Way to Remember

```text
Merge  → combine histories
Rebase → move commits
```

---

# Interactive Rebase

Interactive rebase allows you to **edit, reorder, combine, or delete commits**.

### Command

```bash
git rebase -i HEAD~3
```

This opens an editor showing the last **3 commits**.

Example:

```text
pick a1b2c3 Added login
pick b2c3d4 Fixed bug
pick c3d4e5 Updated UI
```

You can change commands like:

```text
pick
reword
squash
drop
```

---

## Common Interactive Rebase Options

| Command | Purpose               |
| ------- | --------------------- |
| pick    | keep commit           |
| reword  | change commit message |
| squash  | combine commits       |
| drop    | delete commit         |

---

## Example

Combine commits:

```text
pick a1b2c3 Added login
squash b2c3d4 Fix login bug
```

Now both commits become **one commit**.

---

# Rewriting History

Rebase rewrites Git history.

Example:

Before:

```text
A → B → C → D
```

After rebase:

```text
A → B → C → D'
```

Commit IDs change because Git **creates new commits**.

---

## Important DevOps Rule

Never run rebase on **shared branches like main**.

Only use it on:

```text
feature branches
```

Because rewriting history can break other developers' work.

---

# Real DevOps Workflow Using Rebase

Typical workflow:

```text
main branch updated
        ↓
developer updates feature branch
        ↓
git fetch
git rebase main
        ↓
resolve conflicts
        ↓
git push
```

This keeps feature branch **up-to-date with main**.

---

# When to Use Rebase

Use rebase when:

* cleaning commit history
* updating feature branch with latest main
* preparing commits before merge

Avoid rebase when:

* branch is shared
* working on production branch

---

# 30-Second Interview Answer

You can say this confidently:

> Git rebase is used to move commits from one branch to another base commit to maintain a linear history. Unlike git merge, which creates a merge commit, rebase rewrites commit history by applying commits on top of the latest branch. Interactive rebase allows developers to edit, reorder, or squash commits. Rebase should be used on feature branches but avoided on shared branches like main.

---