# Git Tutorial: Step-by-Step Guide
This tutorial explains the basic Git commands to help you create a repository, track changes, and view commit history.

## 1. Initialize a Git repository
```
git init
git config user.name ""
git config user.email ""
```

## 2. Add Files and Make Your First Commit
Commit should written in imperative mood: Think of it as: "If applied, this commit will do what?"

- Upgrade packages
- Fix thread allocation
- Improve mobile responsiveness
```
git add .
git commit -m "Initialize project with basic setup"
```

## 3. Connect to a Remote Repository (GitHub, GitLab, etc.)
```
git remote add origin https://github.com/your-username/your-repo.git
```

## 4. Push Your Code to the Remote
```
git push -u origin main
```

## 5. View the commit history
```
git log
```
Press q to exit the log viewer

## 6. View a Previous Commit (Read-Only / Detached HEAD
```
git checkout <commit-hash>
```
❗ Avoid committing while in detached HEAD. Create a new branch if needed.

##  7. Create and Switch to a New Branch
✅ Shortcut: creates and switches at once.
```
git checkout -b development
```

## 8. Create a Branch (but stay on current one)
```
git branch feature-branch
```

## 9. Switch to an Existing Branch
```
git checkout feature-branch
```

## 10. Push a Feature Branch to Remote
```
git push -u origin feature-branch
```

## 11. Pull Remote Changes Into Local
🧠 This is fetch + merge. It updates your working branch immediately.
```
git pull
```

## 12. Fetch Remote Changes Without Merging
```
git fetch
git checkout development
git merge origin/development
```

## 13. Pull All Remotes and Branches (Manual Merge)
```
git fetch --all
git checkout branch-name
git pull
```

## 14. Reset (Uncommit or Undo)
### 14.1 Undo last commit but keep changes unstaged
```
git reset HEAD~1
```

### 14.2 Undo commit but keep changes staged
```
git reset --soft HEAD~1
```

### 14.3 Delete commit and discard changes (⚠️ irreversible)
```
git reset --hard HEAD~1
```

## 15. Feature Branch Workflow and Pull Request
### Step 1: Create and switch to your feature branch
```
git checkout -b feature-branch
```

### Step 2: Push it to the remote
```
git push -u origin feature-branch
```

### Step 3: Make your changes and commit
```
git add .
git commit -m "Add login validation"
```

### Step 4: Push the latest changes
```
git push
```

### Step 5: Go to GitHub and open a Pull Request (PR)
```
✅ Fill in:
A clear title (e.g., “Fix form validation and update UI”)
A short description of the changes
```

### Step 6: After merge, delete your branch locally
```
git branch -d feature-branch
```

## 16. Merge Conflict Demo (Optional Practice)
### Step 1
```
mkdir git-conflict-demo
cd git-conflict-demo
git init
echo "Hello World" > README.md
git add .
git commit -m "Initial commit"
```

### Step 2
```
git checkout -b branch-a
echo "This is branch A" >> README.md
git add .
git commit -m "Update from branch A"
```

### Step 3
```
git checkout main
echo "This is MAIN branch" >> README.md
git add .
git commit -m "Update from main"
```

### Step 4
```
git merge branch-a
# Conflict will occur.
```

### Step 5
```
git add README.md
git commit -m "Resolve conflict between main and branch-a"
```
