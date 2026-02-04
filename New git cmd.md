# Git & Terminal Command Reference

My personal cheatsheet for essential Git commands and terminal navigation.

---

## Terminal Navigation Basics

| Command | What it does | Example |
|---------|-------------|---------|
| `pwd` | Print working directory (shows where you are) | `pwd` |
| `ls` | List files and folders in current directory | `ls` |
| `ls -la` | List all files including hidden ones, with details | `ls -la` |
| `cd folder-name` | Change into a folder | `cd projects` |
| `cd ..` | Go up one level | `cd ..` |
| `cd ~` | Go to home directory | `cd ~` |
| `mkdir folder-name` | Create a new folder | `mkdir new-project` |

---

## Basic Git Workflow
```bash
git status                    # Check what changed
git add .                     # Stage all changes (or git add filename)
git commit -m "your message"  # Commit with descriptive message
git push                      # Push commits to remote repository
git pull                      # Get latest changes from remote
```

---

## Git Branching

### Creating & Switching Branches
```bash
git branch                    # List all branches (* shows current)
git checkout -b feature-name  # Create AND switch to new branch
git checkout branch-name      # Switch to existing branch
git switch branch-name        # Newer way to switch branches
```

### Merging Branches
```bash
git checkout main             # Switch to branch you want to merge INTO
git merge feature-name        # Merge feature-name into current branch
```

### Deleting Branches
```bash
git branch -d feature-name    # Delete branch (safe - warns if unmerged)
git branch -D feature-name    # Force delete branch
```

---

## Useful Git Commands
```bash
git log                       # View commit history
git log --oneline             # Compact commit history
git diff                      # See unstaged changes
git clone <url>               # Clone a repository
git remote -v                 # View remote repository URLs
```

---

## Common Scenarios

### Made a mistake in last commit message?
```bash
git commit --amend -m "new message"
```

### Want to undo changes to a file?
```bash
git checkout -- filename      # Discard changes in working directory
```

### Need to stash changes temporarily?
```bash
git stash                     # Save changes for later
git stash pop                 # Bring back stashed changes
```

---

## Notes to Self

- Always check `git status` before committing
- Commit messages should be descriptive: "Add login feature" not "update"
- Pull before pushing to avoid conflicts
- Create branches for new features, keep `main` clean


## Practice Notes
   - Created my first branch: test-branch ✓