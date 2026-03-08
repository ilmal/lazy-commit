# gits — lazy commit

A tiny bash script that:
- Stages all changes
- Generates a clean, ultra-short commit message (max 8 words)
- Commits and pushes automatically
- `gits -r` review mode with instant single-keypress decisions (a/e/c)

The `gits` script lives directly in the repo root, so every `git pull` keeps it automatically up-to-date.

---

## Prerequisites

1. **GitHub Copilot subscription** (with GPT-4.1 access)
2. **GitHub Copilot CLI** installed and authenticated
3. `vim` installed (for the edit option in review mode)
4. You are inside a Git repository

### Install Copilot CLI (if missing)

```bash
curl -fsSL https://gh.io/copilot-install | bash
```

Run `copilot` once interactively to log in with your GitHub account.

### Install vim (if missing)

**Ubuntu / Debian:**
```bash
sudo apt update && sudo apt install vim -y
```

**macOS:**
```bash
brew install vim
```

---

## Setup

The `gits` script is already included in this repository. You only need to do this once.

### 1. Clone the repo

```bash
git clone https://github.com/YOUR_USERNAME/lazy-commit.git
cd lazy-commit
```

### 2. Make the script executable

```bash
chmod +x gits
```

### 3. Add the repo folder to your `$PATH`

Run this from inside the cloned folder — it grabs the current path automatically.

**Ubuntu / Debian (bash — `~/.bashrc`):**
```bash
echo "export PATH=\"$(pwd):\$PATH\"" >> ~/.bashrc
source ~/.bashrc
```

**macOS with zsh — `~/.zshrc`:**
```bash
echo "export PATH=\"$(pwd):\$PATH\"" >> ~/.zshrc
source ~/.zshrc
```

**macOS with bash — `~/.bash_profile`:**
```bash
echo "export PATH=\"$(pwd):\$PATH\"" >> ~/.bash_profile
source ~/.bash_profile
```

> **Tip:** You only need to do this once. The script stays updated forever via `git pull`.

---

## Usage

```bash
gits      # Auto-stage, generate message, commit and push
gits -r   # Review mode — inspect the message before committing
```

### Review Mode (`gits -r`)

```
Suggested commit message:
fix: correct off-by-one in pagination logic

(a)ccept (e)dit (c)ancel:
```

| Key | Action |
|-----|--------|
| `a` | Accept the suggested message and commit |
| `e` | Open in `vim` to edit before committing |
| `c` | Cancel — no commit is made |
