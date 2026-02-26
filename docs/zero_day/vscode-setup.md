# Visual Studio Code Setup with WSL (AI4Devs)

This tutorial shows you how to install and configure Visual Studio Code (VS Code) with Windows Subsystem for Linux (WSL) so you can build and run AI4Devs projects in a clean, Linux-based environment—while still using Windows comfortably.


## Why this matters

**Problem:** Many developer tools, project scripts, and CI environments assume Linux. On Windows, you can hit “it works on my machine” issues, missing packages, or slow setup.

**Practical benefits:** VS Code + WSL lets you:

- Run Linux commands and tools locally (without a heavy virtual machine).
- Use the same workflow you’ll see in most engineering teams.
- Keep your projects consistent with typical deployment/CI environments.

**Professional context:** A lot of real systems run on Linux servers, and VS Code’s WSL workflow is a common way to develop on Windows while using Linux tools. VS Code’s official docs cover working in WSL and launching VS Code from a WSL terminal using `code .`. 

![VS Code](https://i.imgur.com/p0HjIIW.png)


## Prerequisites & learning objectives

**Required knowledge**

- Basic Windows navigation (files/folders).
- Basic terminal concepts (running commands, paths).

**Learning outcomes**

- Install VS Code.
- Install WSL (Ubuntu).
- Connect VS Code to WSL.
- Set up core dev tools (Python, venv, Git).
- Understand where to store projects for good performance.


## 1. Install Visual Studio Code

- Download: https://code.visualstudio.com/
- During installation, enable:
  - “Add to PATH”
  - Context menu options like “Open with Code” (nice to have)

**Expected outcome:** VS Code opens normally, and you can run `code` from a terminal.


## 2. Install WSL + Ubuntu

Open **PowerShell as Administrator** and run:

```powershell
wsl --install
```

Microsoft’s WSL docs describe `wsl --install` as the single-command setup that enables required features and installs the default Ubuntu distribution. 

After installation:

- Restart if prompted
- Ubuntu will open and ask you to create a Linux username/password

Verify:

```powershell
wsl --list --verbose
```

## 3. Connect VS Code to WSL

### Install the WSL extension
In VS Code:

- Extensions (`Ctrl + Shift + X`)
- Install **“WSL”** / **“Remote - WSL”** (Microsoft)

### Open a WSL-connected window
Two common ways:

**Option A (recommended): from WSL terminal**
Open Ubuntu (WSL), go to your project folder, then:

```bash
code .
```

VS Code’s WSL tutorial shows using `code .` to open the current folder in VS Code from within WSL. 

**Option B: from VS Code**

- `Ctrl + Shift + P`
- Run: “WSL: New WSL Window”

**Expected outcome:** You see a WSL indicator (e.g., “WSL: Ubuntu”) in the bottom-left of VS Code.


## 4. Set up your Linux dev tools (inside WSL)

Open the VS Code terminal (while connected to WSL) and run:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y python3 python3-pip python3-venv git curl wget
```

Verify:

```bash
python3 --version
pip3 --version
git --version
```

!!! tip
    Use a virtual environment per project when installing Python packages.
    It keeps dependencies clean and avoids breaking other projects.

Example:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
```

## 5. Put projects in the right place (performance)

You *can* access Windows files from WSL at paths like:

```bash
/mnt/c/Users/<you>/...
```

WSL documentation notes that performance is better when you store project files in the Linux filesystem (the `\\wsl$` drive / your Linux home folder) instead of working under `/mnt/`. 

Recommended:

```bash
mkdir -p ~/projects
cd ~/projects
```

Then clone repos there:

```bash
git clone https://github.com/<org-or-user>/<repo>.git
cd <repo>
code .
```

!!! warning
    If your repo is under `/mnt/c/...`, Git operations and file watching can feel slow.
    Move it into `~/projects/` inside WSL when possible.


## 6. VS Code essentials for AI4Devs

Install (in your WSL VS Code window):

- Python (Microsoft)
- (Optional) Markdown tools if you write lots of docs
- (Optional) GitHub Pull Requests (helps with PRs)

Useful shortcuts:

- `Ctrl + Shift + P`: command palette
- `Ctrl + ``: terminal
- `Ctrl + Shift + E`: file explorer
- `Ctrl + B`: toggle sidebar

> Remember: First make it work. Then make it clean. Then commit it.

