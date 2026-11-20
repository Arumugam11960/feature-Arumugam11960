
# Day 2 — Advanced Git & GitHub Management
==========================================


## 1. Git Reset
===============
   * `git reset` moves the current branch pointer (`HEAD`) backward to a specified commit. 
   *  Depending on the flag used, it can also alter your **staging area (index)** and **working directory**.

### Types of Git Reset

**Soft Reset (`--soft`)**: 
--------------------------
    ->Moves `HEAD` to the target commit while keeping all changes **staged** and present in the **working directory**. 
    
     Useful for amending or re-grouping commits cleanly.

**Mixed Reset (`--mixed`, default)**: 
------------------------------------
    ->Moves `HEAD` to the target commit and **unstages** changes, keeping them in the **working directory**.

**Hard Reset (`--hard`)**: 
-------------------------
    ->Moves `HEAD` to the target commit and **discards** all changes in both the **staging area** and **working directory**. *(Destructive — use with care.)*

### Examples
``bash
# Undo the last commit, keep changes staged

    git reset --soft HEAD~1

# Undo the last commit, keep changes unstaged in working directory

    git reset HEAD~1

# Undo the last 2 commits and permanently discard all local changes

    git reset --hard HEAD~2

# Reset current branch to a specific commit hash

    git reset --hard a1b2c3d

Git Revert:
===========

    git revert creates a new commit that applies the inverse of an existing commit's changes. 
    
    It does not rewrite or erase commit history, making it safe for shared or public branches.

How It Works:
--------------
    > Inspects the target commit and calculates the opposite diff.

    > Generates a new revert commit on top of the current branch.

    > Preserves full audit history showing both the original commit and why it was undone.

Examples:-
----------
Bash
# Revert the most recent commit (opens editor for commit message)

   > git revert HEAD

# Revert a specific commit without opening the editor
   
    > git revert --no-edit a1b2c3d

# Revert a merge commit (specify parent 1 for mainline branch)
   
    > git revert -m 1 <merge-commit-hash>

3. Reset vs Revert:-
--------------------

    Both git reset and git revert are Git commands used to undo changes, but they work differently.

    
Git Reset:
----------
   
    > git reset moves the current branch to an earlier commit, effectively removing later commits from the branch's current history.

Syntax:
-------
```bash

    => git reset <commit-id>


There are three main types:
---------------------------
A. Soft Reset
=============:

   => git reset --soft HEAD~1

   - Removes the latest commit from the current branch history.

   - Keeps changes staged.

   - Files remain modified and ready to commit again.

B. Mixed Reset (Default)
========================:

   => git reset --mixed HEAD~1
    
    - Removes the latest commit from branch history.

    - Keeps changes in the working directory.

    - Unstages the changes.

C.Hard Reset
=============:

    =>git reset --hard HEAD~1
    
    - Removes the latest commit from branch history.
    
    - Discards changes from the working directory and staging area.

    - Can cause loss of uncommitted work.

    * Be careful with --hard because it can permanently discard uncommitted changes.


Git Revert
----------:

  *  git revert undoes the changes introduced by a particular commit by creating a new commit.

Syntax:
-------


    bash
    
    git revert <commit-id>

Squash Multiple Commits into One
----------------------------------:

    Git provides the interactive rebase command to squash commits.

Syntax:
---------

bash
    
    git rebase -i HEAD~N

    Here, N represents the number of recent commits you want to combine.

Example Using Interactive Rebase
================================

    Suppose your Git history contains these four commits:

    bash
    
    git log --oneline

Output:
--------

d4e5f6g Fix login bug
c3d4e5f Update login styling
b2c3d4e Add login validation
a1b2c3d Create login page



What is Cherry Pick:
------------------

    Git Cherry Pick is used to apply a specific commit from one branch to another branch without merging the entire branch.

    It is useful when you want to bring only a particular bug fix or feature from another branch.

Syntax
-------:

bash

    git cherry-pick <commit-hash>

Example
-------
Suppose you have two branches:

   > main – Main development branch.

   > feature – Feature development branch.
    
    You have made three commits in the feature branch, but you want to apply only one specific commit (abc1234) to the main branch.

Step 1: Switch to the target branch
----------------------------------
bash

    git checkout main

6. Git Rebase
=============

Definition
----------
   -> Git Rebase is a Git command used to reapply commits from one branch on top of another branch.

    It moves the starting point of a branch to a new base commit, creating a cleaner and more linear project history.
    
Concept of Git Rebase
----------------------:
    
    * Rebase takes the commits from the current branch.
    * It temporarily removes those commits.
    * It moves the branch to the latest commit of the target branch.
    * It reapplies the saved commits one by one on top of the target branch.

Example
--------

    Suppose we have two branches:

    +> main – Main development branch.
    +> feature – Branch where a new feature is developed.

    Initially, the commit history looks like this:
    

        C1 --- C2  (main)
       /
A --- B
       \
        D1 --- D2  (feature)

    Now, the main branch receives a new commit C2, and we want to update the feature branch with the latest changes from main.

Step 1: Switch to the feature branch
-------

bash

    git checkout feature

Step 2: Rebase the feature branch onto main
-------

bash
    git rebase main




Log in
Sign up for free
i want assignment format

Sure! I can prepare your answer in a proper college assignment format.

Standard assignment format
1. Cover Page

College name

Department

Assignment title

Subject name and code

Submitted by (Name, Register Number)

Submitted to (Faculty name)

Academic year

2. Certificate (if required)

3. Acknowledgement

4. Index / Table of Contents

5. Introduction

6. Main Content

Headings and subheadings

Detailed explanations

Examples, diagrams or tables (where needed)

7. Conclusion

8. References / Bibliography

Tell me one thing:
What is your assignment topic?

I'll prepare it in a neat, well-organized college assignment format.


Create a new file in your GitHub repository named Day1.md inside a folder called GitHub/Day1.In this file, write clear notes covering the following topics:
What is DVCS and advantages of over CVCS
(Working Directory → Staging Area → Local Repo → Remote Repo) [with diagram]
Explanation and examples of the following commands:
git add
git commit
git restore
git rm --cached
git log
git log --oneline
Use proper formatting (headings, bullet points, code blocks) so the notes are easy to read.

Worked for 4s
I can prepare the complete Day1.md content, but GitHub needs to be connected before I can create the file directly in your repository.

Below is the exact file structure and content.

GitHub/Day1/Day1.md

Markdown
Writing


Day 1 – Introduction to Git and Version Control
1. What is DVCS?
DVCS (Distributed Version Control System) is a version control system in which every developer has a complete copy of the project's repository, including its history, on their local computer.

Git is one of the most popular examples of a Distributed Version Control System.

Advantages of DVCS over CVCS
CVCS (Centralized Version Control System) stores the project history in a central server, whereas DVCS provides every developer with a complete local repository.


DVCS    CVCS
Every developer has a complete repository copy. Repository is maintained on a central server.
Supports offline work and commits.  Usually requires server access for commits.
Faster local operations.    Some operations depend on network access.
No single central server is required for local history. Central server failure can interrupt collaboration.
Easier to create and merge branches locally.    Branching operations may be more dependent on the server.
Main Advantages of DVCS
Offline Access: Developers can work without an internet connection.
Speed: Most operations happen locally.
Data Safety: Every developer has a complete copy of the repository.
Easy Branching: Creating and merging branches is simple.
Collaboration: Multiple developers can work independently and share changes.
2. Git Workflow
Git follows four major stages when tracking and sharing changes.

Working Directory → Staging Area → Local Repository → Remote Repository
Diagram

text
+---------------------+
|  Working Directory  |
|  (Edit files)       |
+---------------------+
           |
           | git add
           v
+---------------------+
|    Staging Area     |
| (Prepare changes)   |
+---------------------+
           |
           | git commit
           v
+---------------------+
|   Local Repository  |
| (Save permanently)  |
+---------------------+
           |
           | git push
           v
+---------------------+
|  Remote Repository  |
| (GitHub / GitLab)   |
+---------------------+
Explanation of Each Stage
1. Working Directory

It is the folder where we create, edit, and delete project files.
Changes made here are not automatically saved in Git history.
2. Staging Area

It is an intermediate area where changes are selected before committing.
The git add command moves changes into this area.
3. Local Repository

It stores committed changes and project history on the local computer.
The git commit command saves staged changes.
4. Remote Repository

It is a repository hosted on a remote platform such as GitHub.
It allows developers to share and collaborate on projects.
The git push command uploads local commits to the remote repository.
3. Git Commands
3.1 git add
Definition:

The git add command moves changes from the working directory to the staging area.

Syntax:


bash
git add <filename>
Example:


bash
git add index.html
This stages the changes made in index.html.

To stage all modified and untracked files:


bash
git add .
Use: To prepare changes for the next commit.

3.2 git commit
Definition:

The git commit command saves the staged changes into the local repository with a descriptive message.

Syntax:


bash
git commit -m "commit message"
Example:


bash
git commit -m "Added homepage design"
This creates a commit containing the staged changes.

Use: To save a snapshot of the project in Git history.

3.3 git restore
Definition:

The git restore command is used to discard changes in the working directory or remove files from the staging area.

Examples:

To discard unstaged changes in a file:


bash
git restore index.html
To unstage a file while keeping its working-directory changes:


bash
git restore --staged index.html
Use: To restore files or undo staging.

Note: Restoring a file without --staged can permanently discard its unstaged changes.

3.4 git rm --cached
Definition:

The git rm --cached command removes a file from Git tracking while keeping the actual file in the working directory.

Syntax:


bash
git rm --cached <filename>
Example:


bash
git rm --cached config.txt
This removes config.txt from Git's index but keeps it on the computer.

Use:

To stop tracking a file.
To keep local files without including them in the repository.
Commonly used with .gitignore to prevent unwanted files from being tracked.
3.5 git log
Definition:

The git log command displays the commit history of a repository.

Command:


bash
git log
Output includes:

Commit ID (hash)
Author name
Commit date
Commit message
Example:


text
commit a1b2c3d4
Author: Developer
Date: Mon Nov 16 10:00:00 2026

    Added homepage design
Use: To view the complete commit history and track previous changes.

3.6 git log --oneline
Definition:

The git log --oneline command displays commit history in a short and compact format.

Command:


bash
git log --oneline
Example Output:


text
a1b2c3d Added homepage design
b2c3d4e Created README file
c3d4e5f Initial commit
Advantages:

Displays commits in a single line.
Makes history easier to read.
Shows abbreviated commit IDs.
Useful for quickly checking previous commits.
4. Conclusion
Git is a powerful Distributed Version Control System that helps developers manage project versions and collaborate efficiently.

The four stages of Git workflow are Working Directory, Staging Area, Local Repository, and Remote Repository.

Commands such as git add, git commit, git restore, git rm --cached, git log, and git log --oneline help developers manage files, save changes, and view project history.

Understanding these basic Git commands is essential for working with GitHub and managing software development projects.

Next step: Connect your GitHub account using the GitHub connection option. Once connected, I can create GitHub/Day1/Day1.md in your repository.


### 6. Git Rebase
- Explain concept of reapplying commits on top of another branch.
- Provide example.

Add the following section to your Day1.md file.

Writing


6. Git Rebase
Definition
Git Rebase is a Git command used to reapply commits from one branch on top of another branch.

It moves the starting point of a branch to a new base commit, creating a cleaner and more linear project history.

Concept of Git Rebase
Rebase takes the commits from the current branch.
It temporarily removes those commits.
It moves the branch to the latest commit of the target branch.
It reapplies the saved commits one by one on top of the target branch.
Example
Suppose we have two branches:

main – Main development branch.
feature – Branch where a new feature is developed.
Initially, the commit history looks like this:


text
        C1 --- C2  (main)
       /
A --- B
       \
        D1 --- D2  (feature)
Now, the main branch receives a new commit C2, and we want to update the feature branch with the latest changes from main.

Step 1: Switch to the feature branch


bash
git checkout feature
Step 2: Rebase the feature branch onto main


bash
git rebase main

After rebasing, the commit history becomes:
------------------------------------------
A --- B --- C1 --- C2 --- D1' --- D2'  (feature)
                       (main)
Here:
------

   1. D1' and D2' are the reapplied commits.
   2. They have new commit IDs because rebase creates new commits.
   3. The feature branch now contains the latest changes from main.
   4. Handling Merge Conflicts
   5. Sometimes conflicts may occur during rebasing.

Use the following commands:

bash
# Resolve conflicts manually in the affected files

# Mark conflicts as resolved

    git add <filename>

# Continue rebasing

    git rebase --continue


To cancel the rebase:
---------------------
bash

    git rebase --abort

Advantages of Git Rebase
------------------------:

1. Creates a clean and linear commit history.
2. Avoids unnecessary merge commits.
3. Makes project history easier to understand.
4. Keeps feature branches updated with the latest changes.


Git Merge
----------:

Definition:
----------

    Git Merge is a Git command used to combine changes from one branch into another branch.

    It integrates the changes made in different branches while preserving the commit history of both branches.

Concept of Git Merge
====================
    1.Git Merge combines the work of two branches.
    2.It is commonly used to merge feature branches into the main branch.
    3.It preserves the existing commit history.
    4.Git may create a new merge commit to combine the branches.

Example
=======
Suppose we have two branches:

  *  main – Main development branch.

  *  feature – Branch where a new feature is developed.

Initially, the commit history looks like this:

        C1 --- C2  (main)
       /
A --- B
       \
        D1 --- D2  (feature)

    We want to combine the changes from the feature branch into the main branch.

Step 1: Switch to the main branch
-------

bash

    git checkout main

Step 2: Merge the feature branch into main
-------
bash
    git merge feature

After merging, the commit history may look like this:

        C1 --- C2 -------- M  (main)
       /                   /
A --- B                   /
       \                 /
        D1 --- D2 -------
Here:
-----
   1. C1 and C2 represent commits in the main branch.
   2. D1 and D2 represent commits in the feature branch.
   3. M represents the merge commit.
   4. Both branches' changes are combined into the main branch.
   5. Handling Merge Conflicts
   6. Sometimes Git cannot automatically combine changes because the same part of a file has been modified differently in two branches.

These situations are called Merge Conflicts.

Steps to resolve conflicts:
---------------------------
    #Open the conflicted file.
    #Identify the conflicting changes.
    #Edit the file and keep the correct content.
    #Save the file.
    #Stage the resolved file.
    #Complete the merge.

Commands:
------
#bash
    git status
    git add <filename>
    git commit

Advantages of Git Merge
=======================
    Combines changes from different branches.
    Preserves the original commit history.
    Supports parallel development.
    Helps multiple developers work on different features.
    Makes collaboration easier.

Difference Between Git Merge and Git Rebase
--------------------------------------------
    Git Merge                               Git Rebase
Combines two branches.              Reapplies commits on another base.
Preserves branch history.           Creates new commit IDs for reapplied commits.
May create a merge commit.          Usually creates a linear history.
Does not rewrite existing commits.  Rewrites the rebased commits.

GitHub Repository Management
--------------------------

    GitHub Repository Management refers to creating, organizing, securing, and controlling access to repositories hosted on GitHub.

    It helps developers collaborate, manage code, maintain project quality, and protect important branches.

Repository Creation
===================
Definition
----------:

    A GitHub Repository (Repo) is a storage location where project files, source code, documentation, and version history are maintained.

    Repositories can be public or private.

Types of Repositories
--------------------

1. Public Repository
====================

    ->  Anyone can view the repository.
    -> Suitable for open-source projects.
    -> Other developers can contribute through pull requests.

2. Private Repository
======================
    -> Only authorized users can access the repository.
    -> Suitable for personal, company, or confidential projects.

Steps to Create a GitHub Repository
===================================

    1. Log in to your GitHub account.
    2. Click the New Repository option.
    3. Enter the repository name.
    4. Add a description (optional).
    5. Select Public or Private.
    6. Select Initialize with a README file (optional).
    7.Click Create Repository.

Example
---------:
        Repository name: GitHub-Day2-Day2.md

Teams Access and Permission Management
-------------------------------------
Definition
-----------:

    Team Access and Permission Management is the process of controlling who can access a GitHub repository and what actions they can perform.

    GitHub allows repository owners to assign different permissions to team members.

Steps to Set Up Branch Protection
=================================

    1. Open the GitHub repository.
    2. Navigate to Settings.
    3. Select Branches or Rules → Rulesets, depending on the GitHub interface.
    4. Create a branch protection rule or ruleset.
    5. Enter the branch pattern, such as main.
    6. Enable required protections, such as pull request reviews and status checks.
    7. Save the rule.

 CODEOWNERS File Usage
======================
Definition
----------:
    
    A CODEOWNERS file is a special file in GitHub that defines which users or teams are responsible for reviewing changes to specific files or directories in a repository.

    When a pull request modifies files covered by CODEOWNERS rules, GitHub can automatically request reviews from the specified owners.

Location of CODEOWNERS File
--------------------------

    The file can be placed in one of the following locations:

    .github/CODEOWNERS
    CODEOWNERS
    docs/CODEOWNERS

    GitHub uses the first valid CODEOWNERS file found in this search order:

   # .github/
   # Repository root
   # docs/

Example CODEOWNERS File
----------------------
Create a file named CODEOWNERS inside the .github folder.

text
# Default owner for all files
* @project-lead

# Frontend files
*.html @frontend-team
*.css @frontend-team
*.js @frontend-team

# Backend files
*.py @backend-team

# Documentation files
docs/ @documentation-team

# Configuration files
.github/ @project-admin

SSH Key Setup
-------------

    SSH (Secure Shell) keys allow you to connect to GitHub securely without entering your username and password every time you push or pull code.

1. Generate an SSH Key
======================:

Step 1: Open Terminal

    Open your terminal (Linux/macOS) or Git Bash (Windows).

Step 2: Generate the SSH key

    Run the following command:

##bash
    
   *  <ssh-keygen -t ed25519 -C "your_email@example.com">

    Replace your_email@example.com with your GitHub email address.

Step 3: Choose the file location
--------------------------------
When prompted:
------------
text

    Enter file in which to save the key:

    Press Enter to use the default location:

text
     <~/.ssh/id_ed25519>

Step 4: Set a passphrase
------------------------
    You'll be asked to enter a passphrase.

       -> Enter a passphrase for additional security.
        
       -> Or press Enter twice to continue without one.

Your SSH keys will be generated:
-------------------------------
   -> id_ed25519 – Private key (Never share this).

   -> id_ed25519.pub – Public key (Add this to GitHub).

2. Add SSH Key to SSH Agent
---------------------------:
Step 1: Start the SSH agent

    # bash
    # eval "$(ssh-agent -s)"

Step 2: Add your private key

    # bash
    # ssh-add ~/.ssh/id_ed25519

3. Add SSH Key to GitHub
------------------------:

Step 1: Copy your public key
-------
Run:


   # bash
    cat ~/.ssh/id_ed25519.pub
    
    Copy the entire output. It should look similar to:

   (ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAA... your_email@example.com)

Step 2: Open GitHub
-------

1. Log in to your GitHub account.

2. Click New SSH key.

3. Enter a title (e.g., My Laptop).

4. Select Authentication Key as the key type.

5. Paste your copied public key into the Key field.

6. Click Add SSH key.

7. Confirm your GitHub password if prompted.

Webhooks
=========
1. What are Webhooks?
----------------------:

       -> A webhook is a mechanism that allows one application to automatically send real-time information to another application when a specific event occurs.

       -> In simple terms, a webhook is an automatic notification sent from one system to another when something happens.

       -> Webhooks are also called HTTP callbacks or event-driven notifications.
    
Webhooks generally work in the following steps:
================================================

    -> Event occurs: Something happens in an application.

    -> Trigger: The application detects the event.

    -> HTTP request: The application sends an HTTP POST request to a predefined URL.

    -> Receive data: The receiving application gets the information, usually in JSON format.

    -> Action: The receiving application processes the data and performs the required task.

2. Uses of Webhooks
--------------------:

    -> Webhooks are commonly used in CI/CD, notifications, and application integrations.

CI/CD:-> Automating software builds, tests, and deployments.
------:

Notifications:-> Sending instant alerts and messages.
-------------:

Integrations:-> Connecting different applications and synchronizing data.
-------------:

---------------------------------------------------------------------------------------------------------------


