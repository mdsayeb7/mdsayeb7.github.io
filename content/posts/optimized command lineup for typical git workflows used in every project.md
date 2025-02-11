---
title: 'Optimized command lineup for typical Git workflows used in every project'
date: 2024-12-08T03:12:00.016+06:00
draft: false
tags: ['Github']
---

### **Set Up Git and Initialize Repository**

\# Set your Git username and email

`git config --global user.name "Your Name" git config --global user.email "your_email@example.com"  # Initialize a Git repository (if not already done) git init  # Add all files to the staging area git add .  # Commit the initial files git commit -m "Initial commit"  # Add your GitHub repository as a remote git remote add origin https://github.com/<your-username>/<your-repo-name>.git  # Push your code to the main branch git push -u origin main` 

### **Create and Work on a New Branch**

`# Create and switch to a new branch git checkout -b <branch-name>  # Add all files and commit changes git add . git commit -m "Your commit message"  # Push the branch to the remote repository git push -u origin <branch-name>`

### **Merge Branch into Main**

`# Switch to the main branch git checkout main  # Merge the feature branch into main git merge <branch-name> -m "Merge <branch-name> into main"  # Push the merged changes to the remote repository git push origin main`

### **Pull Latest Changes from Main**

`# Pull the latest changes from the remote repository git pull origin main`

### **Clean Up**

`# Delete a branch locally after merging git branch -d <branch-name>  # Delete a branch remotely git push origin --delete <branch-name>`

### **Rollback to Last Commit**

`# Discard changes to a specific file git checkout -- <filename>  # Discard all uncommitted changes git reset --hard  # If needed, reset to a specific commit git reset --hard <commit-hash>`

### **Add `.gitignore` for Ignoring Files**

`# Create a .gitignore file touch .gitignore  # Example entries for a .gitignore file echo "node_modules/" >> .gitignore echo ".env" >> .gitignore echo "dist/" >> .gitignore  # Add and commit the .gitignore file git add .gitignore git commit -m "Add .gitignore"`

### **One-Liner Setup for a New Repository**

For a fresh project setup, this single block of commands can be used:

`git init && git config --global user.name "Your Name" && git config --global user.email "your_email@example.c`

  

 Cleaning up and verifying your Git configuration
nano ~/.gitconfig 
Your file should ideally look like this:
\[user\]
    name = Your Name
    email = your\_email@example.com
Delete all other entries.
Save and Exit
Press Ctrl+O to save changes.
Press Enter to confirm the file name.
Press Ctrl+X to exit Nano.

Create Files ex: touch index.html 

Roll back one file to the last committed state: 
git checkout index.html 

Roll back all files: 
git checkout -f 

Hard reset to the last commit: git reset --hard 

Create a .gitignore file to specify files and folders to be ignored by Git: 
touch .gitignore

Switch to an existing branch:
git checkout branch\_name

Merge Branches
git merge branch\_name -m "Merge message"