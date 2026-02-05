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

## Pull Requests (PRs)

Pull Requests are how teams review code before merging into main.

### PR Workflow:
1. Create branch: `git checkout -b feature-name`
2. Make changes and commit
3. Push branch: `git push -u origin feature-name`
4. Go to GitHub and click "Compare & pull request"
5. Add description, request reviewers
6. Team reviews and approves
7. Merge on GitHub
8. Delete branch after merging

### Why use PRs?
- Code review catches bugs
- Team discusses changes
- Keeps main branch clean and stable


## Merge Conflicts

Merge conflicts happen when two branches change the same line of code differently.

### How to resolve:
1. Git will mark the conflict in your file like this:
```
   <<<<<<< HEAD
   Your changes
   =======
   Their changes
   >>>>>>> branch-name
```
2. Edit the file to keep what you want
3. Remove the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
4. Save the file
5. `git add .`
6. `git commit -m "Resolve merge conflict"`

### Tips:
- Communicate with your team to avoid conflicts
- Pull from staging regularly to stay updated
- Use a merge tool if conflicts are complex


## Git Stash

Temporarily save changes without committing when you need to switch branches.

### Basic commands:
```bash
git stash              # Save current changes
git stash pop          # Restore and remove from stash
git stash list         # See all stashed changes
git stash apply        # Restore but keep in stash
git stash drop         # Delete a stash
```

### When to use stash:
- Need to switch branches but not ready to commit
- Want to pull latest changes but have uncommitted work
- Quickly test something on a clean state


## Three-Tier Branching Strategy

Professional teams use a three-tier system to manage code safely.

### The Three Branches:

#### 1. Main/Master (Production)
- The live code that users see
- Always stable and working
- Never work directly on main
- Only merge from staging after testing

#### 2. Staging (Testing)
- Where all features come together for testing
- Test everything works together before going live
- Merge feature branches here first
- Acts as a "dress rehearsal"

#### 3. Feature Branches (Development)
- Where you build new features
- One branch per feature or task
- Branched from staging
- Examples: `login-page`, `add-search`, `fix-navbar`

### Workflow:
```bash
# 1. Create feature branch from staging
git checkout staging
git pull
git checkout -b new-feature

# 2. Work and commit
git add .
git commit -m "Add new feature"

# 3. Push and create PR to staging
git push -u origin new-feature

# 4. After review, merge to staging
# 5. Test in staging
# 6. When stable, merge staging → main
```

### Why use this system?
- Keeps production stable
- Allows testing before going live
- Team can work on multiple features simultaneously
- Easy to rollback if something breaks