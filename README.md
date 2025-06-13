# Git Tutorial: Step-by-Step Guide
This tutorial explains the basic Git commands to help you create a repository, track changes, and view commit history.

## 1. Initialize a Git 
✅ To check if the Git user is correctly configured in your current folder
git config user.name
git config user.email
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
git add . # to stage everything
git add filename
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

##  6. Create and Switch to a New Branch
✅ Shortcut: creates and switches at once.
```
git checkout -b feature-branch
```

## 7. Create a Branch (but stay on current one)
```
git branch feature-branch
```

## 8. Switch to an Existing Branch
```
git checkout feature-branch
```

## 9. Push a Feature Branch to Remote
```
git push -u origin feature-branch
```

## 10. Pull Remote Changes Into Local
🧠 This is fetch + merge. It updates your working branch immediately.
```
git pull
```

## 11. Fetch Remote Changes Without Merging
```
git fetch
git checkout development
git merge origin/development
```

## 12. Pull All Remotes and Branches (Manual Merge)
```
git fetch --all
git checkout branch-name
git pull
```

## 13. Reset (Uncommit or Undo)
### 13.1 Undo last commit but keep changes unstaged
```
git reset HEAD~1
```

### 13.2 Undo commit but keep changes staged
```
git reset --soft HEAD~1
```

### 13.3 Delete commit and discard changes (⚠️ irreversible)
```
git reset --hard HEAD~1
```

## 14. Git revert (Practice)
You have:
C3 -- Commit 3
C2 -- Commit 2 ← ❌ you want to revert this one
C1 -- Commit 1

### 1. Find the commit hash of Commit 2:
```
git log --oneline
```

```
a1b2c3d Commit 3
4e1f933 Commit 2
x7y8z9a Commit 1
```

### 2. Revert only Commit 2:
```
git revert 4e1f933
```

### 3. Push the new "revert" commit to remote:
```
git push
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
git checkout development
git pull origin development
git branch -d feature-branch
```

## 16. Merge Conflict Demo (Practice)
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