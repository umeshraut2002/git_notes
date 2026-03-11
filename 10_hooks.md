

---

# 14. Git Hooks (DevOps Automation)

## What are Git Hooks

**Git hooks** are **scripts that automatically run at specific events in the Git workflow**.

They allow developers or DevOps engineers to **automate tasks before or after Git actions like commit or push**.

These scripts are stored inside the repository’s `.git/hooks` directory.

### Example Location

```text
.git/hooks/
```

Inside this folder Git provides **sample hook scripts**.

Example:

```text
pre-commit.sample
pre-push.sample
post-commit.sample
```

To activate a hook:

1. Remove `.sample`
2. Add script logic

---

### Simple Interview Definition

> Git hooks are scripts that automatically run when specific Git events occur, such as committing or pushing code.

---

# Why Git Hooks Are Important in DevOps

Git hooks help automate development workflows.

Common DevOps uses:

* code quality checks
* automated testing
* security scanning
* formatting code
* preventing bad commits

They improve **code reliability before it reaches the CI/CD pipeline**.

---

# Types of Git Hooks

There are **two categories**:

| Type              | Trigger                  |
| ----------------- | ------------------------ |
| Client-side hooks | Run on developer machine |
| Server-side hooks | Run on Git server        |

Common DevOps hooks are **client-side hooks**.

---

# 1. Pre-commit Hook

The **pre-commit hook runs before a commit is created**.

It can stop the commit if checks fail.

---

## Example Uses

* code formatting
* lint checks
* security scanning
* unit testing

---

## Example Script

```bash
#!/bin/sh
echo "Running lint check..."
npm run lint
```

If lint fails, the commit stops.

---

### Interview Explanation

> A pre-commit hook runs before a commit is created and is used to enforce code quality checks such as linting or testing.

---

# 2. Post-commit Hook

The **post-commit hook runs after a commit is successfully created**.

It cannot stop the commit but can perform automation tasks.

---

## Example Uses

* notify developers
* trigger build scripts
* send commit logs

Example script:

```bash
#!/bin/sh
echo "Commit completed successfully"
```

---

### Interview Explanation

> A post-commit hook runs after a commit is completed and is typically used for notifications or automation tasks.

---

# 3. Pre-push Hook

The **pre-push hook runs before code is pushed to the remote repository**.

It can stop the push if conditions fail.

---

## Example Uses

* run test suite
* check secrets
* verify branch rules

Example script:

```bash
#!/bin/sh
npm test
```

If tests fail:

```text
Push rejected
```

---

### Interview Explanation

> A pre-push hook runs before code is pushed to the remote repository and can prevent pushing code if tests or checks fail.

---

# DevOps Use Cases of Git Hooks

Git hooks are widely used in DevOps pipelines for **automation and quality control**.

Examples:

### 1. Code Quality Checks

Automatically run:

* lint
* formatting
* style checks

Example tools:

* ESLint
* Prettier

---

### 2. Security Scanning

Prevent pushing secrets like:

```text
AWS_SECRET_KEY
API tokens
passwords
```

---

### 3. Automated Testing

Run unit tests before push.

Example:

```bash
npm test
```

---

### 4. CI/CD Integration

Hooks can trigger CI pipelines on platforms like:

* GitHub
* GitLab
* Bitbucket

---

# Git Hooks Workflow in DevOps

Example automation flow:

```text
Developer writes code
        ↓
git commit
        ↓
Pre-commit hook runs lint/tests
        ↓
Commit created
        ↓
git push
        ↓
Pre-push hook runs tests
        ↓
Code pushed
        ↓
CI/CD pipeline triggers build
```

---

# Advantages of Git Hooks

| Advantage       | Description                      |
| --------------- | -------------------------------- |
| Automation      | Reduces manual work              |
| Code quality    | Prevents bad commits             |
| Security        | Stops secrets from being pushed  |
| CI/CD readiness | Integrates with DevOps pipelines |

---

# Limitations

Git hooks run **locally**, so developers can bypass them.

To enforce rules centrally, teams use **server-side hooks or CI/CD pipelines**.

---

# Easy Way to Remember

```text
Pre-commit → before commit
Post-commit → after commit
Pre-push → before pushing code
```

---

# 20–30 Second Interview Answer

> Git hooks are scripts that run automatically during Git events such as commit or push. They are stored in the .git/hooks directory and are used to automate tasks like linting, testing, and security checks. Common hooks include pre-commit, which runs before a commit to enforce code quality, post-commit, which runs after a commit for automation tasks, and pre-push, which runs before pushing code to ensure tests pass.

---