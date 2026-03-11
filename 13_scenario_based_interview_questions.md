

---

# 1. Recover a Deleted Branch

## Scenario

A developer accidentally deletes a branch:

```bash
git branch -D feature-payment
```

But the commits existed earlier.

## Solution

Use **reflog** to recover the commit.

```bash
git reflog
```

Example output

```
a1b2c3 HEAD@{2}: commit: payment feature added
```

Recreate branch

```bash
git checkout -b feature-payment a1b2c3
```

Now the branch is restored.

---

# 2. Wrong Commit Pushed to Production Branch

## Scenario

A developer accidentally pushes code to `main`.

```bash
git push origin main
```

But the code contains a bug.

## Safe Solution (Best for shared repos)

Use **git revert**.

```bash
git revert <commit-id>
git push origin main
```

This creates a new commit that reverses the changes.

---

## Dangerous but sometimes used

```bash
git reset --hard HEAD~1
git push --force
```

But this **rewrites history** and can break other developers’ work.

---

# 3. Resolve Complex Merge Conflict

## Scenario

Two developers edit the same file.

Example conflict:

```text
<<<<<<< HEAD
const port = 3000;
=======
const port = 5000;
>>>>>>> feature-api
```

## Resolution Steps

1. Open file
2. Choose correct code

Example

```javascript
const port = 5000;
```

3. Stage resolved file

```bash
git add server.js
```

4. Complete merge

```bash
git commit
```

---

# 4. Revert Production Deployment

## Scenario

A bad release is deployed to production.

CI/CD pipeline triggered from Git.

## Solution

Rollback to previous commit.

Find commit

```bash
git log
```

Checkout previous stable commit

```bash
git checkout <commit-id>
```

Create rollback commit

```bash
git revert HEAD
```

Push fix

```bash
git push origin main
```

CI/CD will redeploy the stable version.

Often used with tools like:

* Jenkins
* GitHub Actions
* GitLab CI/CD

---

# 5. Git Rollback Strategy in CI/CD Pipelines

## Scenario

Deployment pipeline fails after merging new code.

## DevOps Strategy

1. Identify last stable commit
2. Revert the bad commit
3. Trigger redeployment

Commands

```bash
git revert <bad-commit>
git push origin main
```

Pipeline flow

```
Git Commit
   ↓
CI Build
   ↓
Tests
   ↓
Deployment
```

If failure occurs:

```
Rollback Commit
   ↓
Redeploy previous stable version
```

---

# 6. Accidental Commit to Wrong Branch

## Scenario

Developer commits to `main` instead of `feature-login`.

Fix steps.

Undo commit but keep changes

```bash
git reset --soft HEAD~1
```

Create correct branch

```bash
git checkout -b feature-login
```

Commit again

```bash
git commit -m "login feature"
```

---

# 7. Remove Sensitive Data from Git

## Scenario

A developer accidentally commits an API key.

Example

```
API_KEY=123456
```

## Solution

Remove file

```bash
git rm .env
```

Amend commit

```bash
git commit --amend
```

Add to `.gitignore`

```
.env
```

Push changes.

---

# 8. Fix Commit Message After Push

## Scenario

Commit message contains typo.

If not pushed

```bash
git commit --amend
```

If already pushed

```bash
git commit --amend
git push --force
```

---

# 9. Find Who Changed a Line of Code

## Scenario

Bug appears in production.

Need to know who modified the code.

Use:

```bash
git blame filename
```

Example

```
a1b2c3 (John) const port = 3000;
```

---

# 10. Debugging When CI Pipeline Suddenly Fails

## Scenario

Build pipeline fails after new commits.

Use **git bisect**.

Start bisect

```bash
git bisect start
git bisect bad
git bisect good <old-commit>
```

Git checks commits automatically to locate the bug.

---

# 11. Delete Remote Branch

```bash
git push origin --delete feature-login
```

---

# 12. Sync Local Repository with Remote

```bash
git fetch origin
git reset --hard origin/main
```

---

# 13. Undo Last Commit but Keep Changes

```bash
git reset --soft HEAD~1
```

---

# 14. Undo Last Commit and Delete Changes

```bash
git reset --hard HEAD~1
```

---

# 15. Move Commit to Another Branch

Scenario: commit done on wrong branch.

Steps:

```bash
git cherry-pick <commit-id>
```

---

# 16. View Commit History

```bash
git log
```

Compact format

```bash
git log --oneline
```

---

# 17. Show File Changes Between Commits

```bash
git diff commit1 commit2
```

---

# 18. Check Repository Status

```bash
git status
```

---

# 19. Push Code to Remote

```bash
git push origin main
```

---

# 20. Pull Latest Code

```bash
git pull origin main
```

---

# Quick Interview Tip

Many DevOps interviews expect **scenario answers like this structure**:

1️⃣ Explain the problem
2️⃣ Explain risk
3️⃣ Show Git command
4️⃣ Explain why it works

Example answer:

> "In production I would use **git revert instead of reset**, because revert preserves commit history and avoids breaking other developers’ repositories."

---
