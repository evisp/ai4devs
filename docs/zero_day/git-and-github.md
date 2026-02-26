# Git and GitHub Setup and Essentials 

This tutorial helps you set up Git and GitHub for the AI4Devs program so you can submit projects, collaborate safely, and keep a clean history of your work.

## Why this matters

**Problem:** As soon as you edit code more than once (or work with someone else), it becomes easy to lose changes, overwrite good work, or forget what you tried.

**Practical benefits:** Git and GitHub help you:

- Save your work in small checkpoints (commits).
- Work on features without breaking the main branch (branches).
- Share and review changes through GitHub (pull requests).
- Recover from mistakes (history).

**Professional context:** Most software teams use Git every day. In AI4Devs, you’ll use it to track code, documentation, prompt logs, tests, and fixes—not just “final answers”.

## Prerequisites & learning objectives

**Required knowledge**

- Basic terminal navigation (`cd`, `ls`, editing files).
- A GitHub account.

**Required tools**

- Git installed.
- Terminal (Linux/macOS/WSL or Windows Terminal).
- A code editor (VS Code, etc.).

**Learning outcomes**

- Configure Git with your identity.
- Authenticate to GitHub securely.
- Clone a repository, commit changes, and push them.
- Pull updates and resolve simple conflicts.
- Use a basic branch workflow for safer work.


## 1. Configure your Git identity

Git records who made each commit.

```bash
git config --global user.name "Your Full Name"
git config --global user.email "your-email@example.com"
```

Verify:

```bash
git config --global --list
```

!!! tip
    Use the same email as your GitHub account to keep your contributions consistent.

## 2. Authenticate to GitHub (recommended options)

GitHub no longer accepts account passwords for Git operations over HTTPS. A common approach is using a **Personal Access Token (PAT)** as a password replacement for HTTPS Git operations. 

### Option A: Git Credential Manager or GitHub CLI
GitHub recommends using GitHub CLI or Git Credential Manager (GCM) to remember credentials when using HTTPS. 

- This avoids putting tokens in command history.
- You authenticate once, then Git reuses it securely.

### Option B: Personal Access Token (PAT) for HTTPS
A PAT can be used in place of a password for Git operations over HTTPS. 

Create a PAT:

- GitHub → **Settings → Developer settings → Personal access tokens**
- Generate a token and copy it (you won’t see it again).
- Store it in a password manager or secure note.



## 3. Create your repository on GitHub (clean start)

For Holberton/AI4Devs projects, you will often be given a repository name or you will create one for your notes and docs.

Create a new repository on GitHub:

- Click **New**
- Choose a name (example: `ai4devs`)
- Usually keep it **Public** (unless your cohort requires private)
- Decide if you want a README:
  - If you are starting from scratch locally, you can leave it unchecked.
  - If you want GitHub to create it, check it.

## 4. Clone the repository locally

Copy the HTTPS clone URL from GitHub and run:

```bash
git clone https://github.com/<username>/<repo>.git
cd <repo>
```

Check your remote:

```bash
git remote -v
```

!!! note
    If Git asks for a password with HTTPS, use your PAT as the password (your GitHub username stays the username). 


## 5. The core workflow (edit → stage → commit → push)

This is the pattern you will use daily.

### 1) Make a change
Example:

```bash
echo "# AI4Devs Notes" > README.md
```

### 2) Check status
```bash
git status
```

### 3) Stage changes
```bash
git add README.md
```

### 4) Commit changes
```bash
git commit -m "Add README"
```

### 5) Push to GitHub
```bash
git push origin main
```

!!! tip
    Write commit messages like short actions: “Add…”, “Fix…”, “Update…”.
    It makes the history easier to scan.


## 6. Pull before you push (avoid conflicts)

If you work on multiple machines or with teammates, always pull first:

```bash
git pull
```

If Git reports a conflict:

- Open the conflicted file(s)
- Choose the correct version
- Remove conflict markers
- Commit and push again

## 7. Branches (safe way to work)

Branches let you work without breaking `main`.

Create and switch to a branch:

```bash
git switch -c docs/prompting-debug-assistant
```

Work, commit, then push your branch:

```bash
git push -u origin docs/prompting-debug-assistant
```

Then open a Pull Request on GitHub to merge into `main`.

!!! note
    Use branches when you are making big changes (new module, restructuring docs, major refactor).
    For tiny edits, committing directly to `main` can be fine if you work alone.


## Useful commands (daily)

| Command | Purpose | When to use |
|---|---|---|
| `git status` | See what changed | Before staging/committing |
| `git add <file>` | Stage a file | Before committing |
| `git add .` | Stage everything | When you’re sure all changes belong together |
| `git commit -m "msg"` | Save a checkpoint | After staging |
| `git push` | Upload commits | After committing |
| `git pull` | Download updates | Before starting work / before pushing |
| `git log --oneline --decorate --graph --all` | View history clearly | When you’re lost |


## AI4Devs-specific best practices

- Commit **proof**, not just code: include tests, validation notes, and small logs when relevant.
- Keep sensitive data out of Git:
  - API keys, tokens, `.env`, credentials.
- Use `.gitignore` early (so you don’t accidentally commit build folders 

!!! warning
    Never commit secrets (PATs, API keys, private URLs).
    If you accidentally push a secret, treat it as leaked: revoke/rotate it immediately.

> Remember: A git pull a day keeps the conflicts away.
