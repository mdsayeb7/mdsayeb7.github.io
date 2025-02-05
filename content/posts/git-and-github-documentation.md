---
title: 'Git and GitHub Documentation'
date: 2024-12-08T02:40:00.013+06:00
draft: false
url: /2024/12/git-and-github-documentation.html
tags: 
- Github
---

Installation and Setup
----------------------

1.  **Download Git**  
    Visit [Git Downloads](https://git-scm.com/downloads) and install Git on your system.
    
2.  **Set Up Your Identity**  
    Configure your user name and email:
    
    ```
    
    
    `git config --global user.name "Your Name" git config --global user.email "your_email@example.com"`
    
    
    
    
    
    ```
    
    To configure these settings only for the current repository, omit the `--global` flag:
    
    ```
    
    
    `git config user.name "Your Name" git config user.email "your_email@example.com"`
    
    
    
    
    
    ```
3.  **Check Current Configuration**
    
    ```
    
    
    `git config --global user.name git config --global user.email`
    
    
    
    
    
    ```

* * *

Repository Setup
----------------

1.  **Initialize a Repository**
    
    ```
    
    
    `git init`
    
    
    
    
    
    ```
2.  **Check Hidden Files**
    
    ```
    
    
    `ls -lart`
    
    
    
    
    
    ```
3.  **Create Files**
    
    ```
    
    
    `touch filename.ext ex: touch index.html`
    
    
    
    
    
    ```
4.  **Check Repository Status**
    
    ```
    
    
    `git status`
    
    
    
    
    
    ```

* * *

Staging and Committing Changes
------------------------------

1.  **Add Files to Staging Area**
    
    *   Add a specific file:```
        
        
        `git add index.html`
        
        
        
        
        
        ```
    *   Add all changes:```
        
        
        `git add -A`
        
        
        
        
        
        ```
    *   Add changes in a specific folder:```
        
        
        `cd folder_name git add .`
        
        
        
        
        
        ```
2.  **Commit Changes**
    
    ```
    
    
    `git commit -m "Initial commit"`
    
    
    
    
    
    ```
3.  **Rollback Changes**
    
    *   Roll back one file to the last committed state:```
        
        
        `git checkout index.html`
        
        
        
        
        
        ```
    *   Roll back all files:```
        
        
        `git checkout -f`
        
        
        
        
        
        ```

* * *

Viewing Logs and Comparing Changes
----------------------------------

1.  **Check Commit History**
    
    ```
    
    
    `git log`
    
    
    
    
    
    ```
    *   Show detailed changes for the last commit:```
        
        
        `git log -p -1`
        
        
        
        
        
        ```
    *   Press `Q` to exit the log view.
2.  **Compare Changes**
    
    *   Compare staged changes with the last commit:```
        
        
        `git diff --staged`
        
        
        
        
        
        ```
    *   Do not forget to do stage changes before comparing:```
        
        
        `git add -A`
        
        
        
        
        
        ```
3.  **Reset Repository**
    
    *   Hard reset to the last commit:```
        
        
        `git reset --hard`
        
        
        
        
        
        ```

* * *

Managing Files and Ignoring Changes
-----------------------------------

1.  **Remove Files**
    
    *   Remove a specific file:```
        
        
        `git rm filename.txt`
        
        
        
        
        
        ```
    *   Force remove a file (if errors occur):```
        
        
        `git rm filename.txt -f`
        
        
        
        
        
        ```
2.  **Ignore Files**
    
    *   Create a `.gitignore` file to specify files and folders to be ignored by Git:```
        
        
        `touch .gitignore`
        
        
        
        
        
        ```

* * *

Working with Branches
---------------------

1.  **Check Branches**
    
    ```
    
    
    `git branch`
    
    
    
    
    
    ```
2.  **Create a New Branch**
    
    ```
    
    
    `git branch branch_name`
    
    
    
    
    
    ```
3.  **Switch Between Branches**
    
    *   Switch to an existing branch:```
        
        
        `git checkout branch_name`
        
        
        
        
        
        ```
    *   Create and switch to a new branch:```
        
        
        `git checkout -b branch_name`
        
        
        
        
        
        ```
4.  **Merge Branches**
    
    ```
    
    
    `git merge branch_name -m "Merge message"`
    
    
    
    
    
    ```

* * *

Pushing Changes to a Remote Repository
--------------------------------------

1.  **Push Changes**
    
    ```
    
    
    `git push -u origin branch_name`
    
    
    
    
    
    ```
2.  **Pull Changes**  
    Fetch and merge changes from a remote repository:
    
    ```
    
    
    `git pull origin branch_name   `
    
    
    
    
    ```

* * *

  
here is the overall command line Initialize Git Repository: If you haven't already, initialize a Git repository and commit your changes:  
git init  
git add .  
git commit -m "Initial commit"  
  
Add Remote Repository: Add your GitHub repository as a remote:  

git remote add origin https://github.com/<your-username>/<your-repo-name>.git

  
Push to GitHub: Push your code to the main branch of your GitHub repository:  
git push -u origin main  

Advanced Commands
-----------------

1.  **Stash Changes**  
    Temporarily save uncommitted changes:
    
    ```
    
    
    `git stash`
    
    
    
    
    
    ```
    
    Apply the stashed changes:
    
    ```
    
    
    `git stash apply`
    
    
    
    
    
    ```
2.  **Clone a Repository**
    
    ```
    
    
    `git clone repository_url`
    
    
    
    
    
    ```
3.  **Revert a Commit**
    
    ```
    
    
    `git revert commit_hash`
    
    
    
    
    
    ```
4.  **View Remote Repositories**
    
    ```
    
    
    `git remote -v`
    
    
    
    
    
    ```
5.  **Fetch Changes Without Merging**
    
    ```
    
    
    `git fetch origin branch_name`
    
    
    
    
    
    ```

* * *

Tips
----

*   Always use descriptive commit messages to keep track of changes.
*   Use `.gitignore` to prevent unnecessary files (like logs, environment files) from being tracked.
*   Regularly pull changes from the remote repository to keep your local copy updated.  
      
      
    
    **Pull with** `--allow-unrelated-histories`:
    
      
    
    ```
    git pull origin main --allow-unrelated-histories
    ```