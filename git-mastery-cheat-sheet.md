# Pro Git Mastery Cheat Sheet

## 1. Essential Config & Environment
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global core.editor "nvim"       # or code, vim, nano
git config --global pull.rebase true         # Always rebase on pull
git config --global init.defaultBranch main  # Use main as default branch
git config --global alias.lg "log --oneline --graph --decorate --all"
```
💡 **Tip**: Use `~/.gitconfig` aliases for speed — you can create a whole “git DSL” for yourself.

---

## 2. Branch Power Moves
```bash
git switch -c feature/xyz         # Create & switch to new branch
git switch main                   # Switch to existing branch
git branch -m old new             # Rename branch
git branch --move old new         # Safer rename
git branch --no-merged            # See branches not merged yet
git worktree add ../path branch   # Work on branch in separate dir
```
💡 **Worktree** lets you check out multiple branches *simultaneously*.

---

## 3. Commit Like a Pro
```bash
git commit -m "feat: short msg" -m "Longer description..."
git commit --amend                # Edit last commit
git commit --fixup <commit>       # Mark commit for autosquash
GIT_EDITOR=true git commit --amend --no-edit  # Amend without edit
```
💡 Use **Conventional Commits** (`feat:`, `fix:`, `docs:`, `refactor:`, etc.) for better automation.

---

## 4. Interactive Staging
```bash
git add -p                        # Stage hunks interactively
git restore --staged file         # Unstage
git restore file                  # Discard changes
git stash push -m "msg"           # Save WIP
git stash pop                     # Restore WIP
```
💡 Use **`git stash -p`** to stash only selected hunks.

---

## 5. Rebase & History Surgery
```bash
git rebase -i HEAD~5               # Edit last 5 commits
git rebase --autosquash            # Auto squash fixup! commits
git rebase --onto main featureA    # Move branch from featureA to main
git reflog                         # View every HEAD change
```
💡 `git reflog` is your **time machine** — even for “deleted” commits.

---

## 6. Merge Strategies
```bash
git merge --no-ff feature          # Keep merge commit
git merge --squash feature         # Single commit merge
git cherry-pick <commit>           # Apply specific commit
git cherry-pick -n <commit>        # Apply without committing
```
💡 Use **squash merges** for feature branches to keep history clean.

---

## 7. Remote Repo Mastery
```bash
git remote -v                      # List remotes
git remote add origin url
git fetch --all --prune
git push origin main --force-with-lease
```
💡 **Force-with-lease** prevents overwriting others’ changes.

---

## 8. Advanced Log & Search
```bash
git log --since="2 weeks ago" --author="Scott"
git log --grep="keyword"
git log -S "functionName"          # Search by code changes
git blame file                     # See who changed what
git show <commit>                  # Show commit details
```
💡 Combine **`git log -p`** with `--grep` for code archaeology.

---

## 9. File Recovery & Reset
```bash
git checkout <commit> -- file      # Recover specific file from commit
git reset --soft HEAD~1            # Undo commit, keep changes
git reset --hard HEAD~1            # Undo commit, discard changes
git clean -fd                      # Remove untracked files
```
💡 Use **soft reset** for “undo last commit but keep my work”.

---

## 10. Submodules & Subtrees
```bash
git submodule add url path
git submodule update --init --recursive
git subtree add --prefix=dir url branch --squash
git subtree pull --prefix=dir url branch --squash
```
💡 Prefer **subtrees** over submodules for simpler CI/CD pipelines.

---

## 11. Productivity Aliases (Pro-Level)
In `~/.gitconfig`:
```ini
[alias]
  co = checkout
  sw = switch
  st = status -sb
  cm = commit -m
  amend = commit --amend
  hist = log --pretty=format:'%C(yellow)%h%Creset %ad | %s%d %Cgreen(%an)%Creset' --date=short
  undo = reset --soft HEAD~1
  who = shortlog -sn
```
💡 These cut keystrokes by **70%** over time.

---

## 12. Danger Zone Recovery
```bash
git fsck                         # Check repo integrity
git gc --prune=now --aggressive  # Cleanup repo
git reflog expire --expire=now --all && git gc --prune=now --aggressive
```
💡 If you “destroy” history, **`git fsck` + `git reflog`** can save you.

---

## 13. Git in Quant & Data Projects
- Keep **data outputs** in `.gitignore`
- Use **LFS (Large File Storage)** for datasets:
  ```bash
  git lfs install
  git lfs track "*.csv"
  ```
- Commit **scripts/configs**, not raw data


---


# GitHub Mastery Cheat Sheet

## 1. First-Time GitHub Setup
```bash
# Set your Git identity
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# Check current config
git config --list
```
💡 Make sure your **Git email matches your GitHub account** for commits to be linked.

---

## 2. Connecting to GitHub (HTTPS vs SSH)

### Option A — HTTPS
```bash
git clone https://github.com/user/repo.git
```
- Use **Personal Access Token (PAT)** instead of password:
  - Go to **GitHub → Settings → Developer Settings → Personal Access Tokens → Tokens (classic)**
  - `git push` → enter username + token as password

### Option B — SSH
```bash
ssh-keygen -t ed25519 -C "you@example.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```
Copy public key:
```bash
cat ~/.ssh/id_ed25519.pub
```
Add it in **GitHub → Settings → SSH and GPG keys → New SSH key**  
Test connection:
```bash
ssh -T git@github.com
```

---

## 3. Cloning & Forking
```bash
# Clone your own repo
git clone git@github.com:user/repo.git

# Clone someone else's repo
git clone https://github.com/otheruser/repo.git

# Fork from GitHub UI → clone your fork
```

---

## 4. Keeping Forks Updated
```bash
git remote add upstream https://github.com/original/repo.git
git fetch upstream
git checkout main
git merge upstream/main
```
Or:
```bash
git pull upstream main --rebase
```

---

## 5. Branching for Collaboration
```bash
git checkout -b feature/xyz
# work on changes...
git push origin feature/xyz
```

---

## 6. Pull Requests (PR)
1. Push branch to your fork.
2. Go to GitHub → Compare & pull request.
3. Assign reviewers, add description.
4. Link issues with keywords (`Fixes #42`).
5. After approval → Merge.

---

## 7. Reviewing Code
```bash
# Fetch the PR branch locally
git fetch origin pull/ID/head:pr-branch
git checkout pr-branch
```

---

## 8. GitHub Issues & Project Boards
- Use **`Fixes #<issue_number>`** in commits/PR descriptions to auto-close issues.
- Labels & milestones keep projects organized.
- GitHub Projects (Kanban) for backlog, in-progress, done.

---

## 9. GitHub Actions (CI/CD)
Example `.github/workflows/test.yml`:
```yaml
name: Run Tests
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: 3.11
      - run: pip install -r requirements.txt
      - run: pytest
```

---

## 10. Security Best Practices
- Never commit `.env` files or secrets — add them to `.gitignore`.
- Use **GitHub Secrets** for tokens/passwords in Actions.
- Rotate **Personal Access Tokens** regularly.
- Enable **2FA** on GitHub account.

---

## 11. Advanced Productivity
```bash
# View remote URLs
git remote -v

# Change HTTPS to SSH
git remote set-url origin git@github.com:user/repo.git

# Search GitHub repos from terminal (needs gh CLI)
gh repo list --limit 10
```
Install [GitHub CLI](https://cli.github.com/):
```bash
gh auth login
gh repo clone user/repo
gh pr create --fill
gh issue list
```

---

## 12. Recovering Lost Work
```bash
git reflog
git checkout <commit>
```


