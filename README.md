# Git Tutorial: Step-by-Step Guide
This guide walks you through essential Git commands to manage versions, collaborate in teams, and handle common issues like merges and conflicts.
Each step includes the commands, short explanations, and good commit practices.

## 1. Initialize a Git Repository
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
Use this when you want to see remote updates but not merge yet.
```
# Step 1: Download (fetch) remote changes, don’t modify your local files
git fetch
git checkout development
git merge origin/development
```

## 12. Pull All Remotes and Branches (Manual Merge)
Use this when you want to update everything, not just one branch.
```
# Fetch updates for all remotes and branches
git fetch --all
git checkout branch-name
git pull
```

## 13. Sync Development with Remote (Safe & Common Way)
This is the most typical workflow to keep your development branch up-to-date with remote changes:
```
# switch to your local dev branch
git checkout development
# get latest updates from remote
git fetch origin
# fetch + merge changes into local dev
git pull origin development
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

## 15. Git revert (Practice)
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

## 16. Feature Branch Workflow and Pull Request
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

## 17. Merge Conflict Demo (Practice)
### Create a demo repo and initial commit
```
mkdir git-conflict-demo
cd git-conflict-demo
git init
echo "Hello World" > README.md
git add README.md
git commit -m "Initial commit"
```

### Create branch-a and change the file there
```
git checkout -b branch-a
echo "This is branch A" >> README.md
git add README.md
git commit -m "Update from branch A"
```

What to expect: README.md now has two lines:
```
Hello World
This is branch A
```

### Switch back to main and change the file differently
```
git checkout main   # or `master` if your repo uses that name
echo "This is MAIN branch" >> README.md
git add README.md
git commit -m "Update from main"
```

What to expect: On main the file has:
```
Hello World
This is MAIN branch
```

### Merge branch-a
```
git merge branch-a
# Conflict will occur.
git status
```

### Inspect the conflicted file
Open README.md. You’ll see conflict markers:
```
Hello World
<<<<<<< HEAD
This is MAIN branch
=======
This is branch A
>>>>>>> branch-a
```

### Resolve the conflict manually
Keep main version only:
```
Hello World
This is MAIN branch
```

### Mark resolved and finish the merge
```
git add README.md     # mark as resolved
git commit -m "Resolve conflict: merge branch-a into main"
```

## 18. Rename a local branch:
```
git branch -m juli-feature-branch juli-init
```

## 19. Reset to the remote version to drop them:
```
git reset --hard origin/development
```

## 20. See current branch:
```
git branch --show-current
```

## 21. Check remote URLs:
```
git remote -v
```

## 22. Delete a Remote Branch (after merge):
```
git push origin --delete feature-branch
```