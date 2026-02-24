# How to Setup Openclawd on Mac mini M4

This guide walks you through a clean, practical setup of **Openclawd** on a **Mac mini M4**.

---

## 1) Prerequisites

Before installing, make sure you have:

- macOS updated (recommended: latest stable)
- Admin access on the Mac mini
- Stable internet connection
- GitHub account (for repo/docs updates)

Optional but recommended:

- Terminal familiarity
- API keys for tools you plan to use (OpenAI, Anthropic, etc.)

---

## 2) Install Homebrew (if needed)

Open Terminal and run:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then verify:

```bash
brew --version
```

---

## 3) Install core dependencies

Install common dependencies used by Openclawd workflows:

```bash
brew install git node pnpm
```

Check versions:

```bash
git --version
node -v
pnpm -v
```

---

## 4) Install Openclaw CLI

Install globally with npm:

```bash
npm install -g openclaw
```

Verify install:

```bash
openclaw --version
openclaw help
```

---

## 5) Initialize Openclaw workspace

Create your workspace directory and enter it:

```bash
mkdir -p ~/.openclaw/workspace
cd ~/.openclaw/workspace
```

Check service/health status:

```bash
openclaw status
```

Gateway controls (if needed):

```bash
openclaw gateway status
openclaw gateway start
```

---

## 6) Configure credentials and environment

Set required API keys in your shell profile (`~/.zshrc`) or Openclaw config method:

```bash
export OPENAI_API_KEY="your_key_here"
# add others as needed
```

Reload shell:

```bash
source ~/.zshrc
```

Confirm Openclaw can see your setup:

```bash
openclaw status
```

---

## 7) Clone your GitHub repo for docs/reference

Example:

```bash
cd ~/.openclaw/workspace
git clone https://github.com/<your-user-or-org>/Openclaw.git github/Openclaw
cd github/Openclaw
```

If already cloned, pull latest:

```bash
git pull
```

---

## 8) Create/update documentation in `docs/reference`

Create a reference file:

```bash
mkdir -p docs/reference
nano docs/reference/how_to_setup_openclawd_on_mac_mini_m4.md
```

Paste your steps, save, and exit.

---

## 9) Commit and push to GitHub

From repo root:

```bash
git add docs/reference/how_to_setup_openclawd_on_mac_mini_m4.md
git commit -m "docs(reference): add Mac mini M4 Openclawd setup guide"
git push
```

---

## 10) Verify setup works end-to-end

Quick sanity checks:

```bash
openclaw status
openclaw gateway status
openclaw hooks list
```

If something fails, capture logs/output and troubleshoot from there.

---

## Troubleshooting (quick)

- **`openclaw: command not found`**
  - Ensure npm global bin is in PATH.
- **Gateway not running**
  - Run `openclaw gateway start`, then re-check status.
- **Git push rejected**
  - Pull/rebase first or verify repo permissions.
- **Permission errors**
  - Avoid `sudo` unless absolutely required; fix ownership instead.

---

## Recommended next hardening steps

- Enable periodic `openclaw status` checks.
- Keep macOS + Homebrew packages updated.
- Store secrets securely (avoid committing keys).
- Add backup/export routines for critical workspace files.

---

If you want, I can also create a **short version** of this guide for quick onboarding and a **checklist version** for repeat setups.