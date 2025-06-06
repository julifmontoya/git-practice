# Git Tutorial: Step-by-Step Guide

This tutorial explains the basic Git commands to help you create a repository, track changes, and view commit history.

#### 1. Initialize a Git repository
```
git init
git config user.name ""
git config user.email ""
```

#### 2. Add all files to the staging area
```
git add .
```

#### 3. Commit the changes
 Written in imperative mood: Think of it as: "If applied, this commit will do what?"

- Upgrade packages
- Fix thread allocation
- Improve mobile responsiveness
```
git commit -m "Initialize project with basic setup"
```

#### 4. Connect to a remote repository (like GitHub)
```
git remote add origin https://github.com/your-username/your-repo.git
```

#### 5. Push the changes to GitHub
```
git push -u origin main
```

#### 6. View the commit history
```
git log
```

#### 7. Go back to a previous commit (read-only)
You're looking at the code as it was at that commit — like a snapshot. This is called a detached HEAD state (you're not on any branch).
🧠 Note: You can explore the code here, but avoid making commits unless you create a branch (see step 9).

```
Copy the commit hash, for example: "7a2aeb77d30536aa37bc51902c08eb128ad83b2b"
Press q to exit the log.
Then check out the old commit:
git checkout 7a2aeb77d30536aa37bc51902c08eb128ad83b2b
```

#### 8. Create a new branch (but stay on the current one)
```
git branch development
```

#### 9. Create and switch to a new branch in one step
```
git checkout -b development
```

#### 10. Switch to an existing branch
```
git checkout 'branch-name'
```

#### 11. Push your feature branch to the remote
```
git push -u origin feature-branch
```

#### 12. Integrate remote changes into your local code = fetch + merge automatically
It downloads changes and immediately applies them to your current branch. So your local files get updated right away.
```
git pull
```

#### 13. checks for new changes but does not integrate them automatically.
just downloads changes from the remote, but does NOT change your files
```
git fetch                     # Download new commits from remote, but no merge
git checkout development      # Switch to development branch (local)
git merge origin/development  # Manually merge the remote changes into local
```

#### 14. To pull everything (in simple terms):
Step 1: Download latest data from all remotes (but don’t merge)
```
git fetch --all 
```

Step 2: Switch to the branch you want to update
```
git checkout branch-name 
```

Step 3: Merge the latest changes into your branch
```
git pull
```

#### 15.1 git reset --soft
You want to change the last commit message.
You forgot to add something before committing.
```
git reset --soft <hash>
git commit -m "New message"
```

#### 15.2 git reset --mixed 
Undo last commit, unstage the files, but keep your code changes
```
git reset --mixed <hash>
```

#### 15.3 git reset --hard 
Undo last commit AND discard all related code changes
```
git reset --hard <hash>
```

#### 16. Full Instructions to Push and Make a Pull Request
Create and switch to your feature branch
```
git checkout -b feature-branch
```

Make your changes
```
git add .
git commit -m "Add new feature or update"
```

Push your feature branch to the remote
```
git push -u origin feature-branch
```

Go to GitHub (or GitLab/Bitbucket)
```
“Compare & pull request” or “Create pull request”
```

Fill in the Pull Request (PR) form
```
Add:
meaningful title
short description of what the PR does
```

Create the PR
```
Click "Create Pull Request"
```

Review & Merge (once ready)
```
You (or your team) review the code
When approved, click "Merge Pull Request"
```

#### 17. Simple Merge Conflict Exercise
📦 1. Create a test folder
```
mkdir git-conflict-demo
echo Hello World > README.md
git add README.md
git commit -m "Initial commit"
```

🌿 2. Create branch-a and make a change
```
git checkout -b branch-a
echo This is branch A >> README.md
git add README.md
git commit -m "Update from branch A"
```

🏠 3. Go back to master and create a conflicting change
```
git checkout master
echo This is MASTER branch >> README.md
git add README.md
git commit -m "Update from master"
```

🔥 4. Merge branch-a into main (conflict happens!)
```
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

🛠 5. Open README.md and manually fix the conflict
```
Hello World
This is MAIN branch
This is branch A
```

📥 6. Stage and commit the resolved file
```
git add README.md
git commit -m "Merge branch-a into main and resolve conflict"
```