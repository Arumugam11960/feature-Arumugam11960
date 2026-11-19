
day 1: Git & Version Control Fundamentals
=========================================
#1. Distributed Version Control System (DVCS) vs. Centralized Version Control System (CVCS)

#What is a DVCS?
================
A**Distributed Version Control System (DVCS)*
--------------------------------------------
    such as Git or Mercurial—is a system where every developer has a complete, local copy (clone) of the entire repository, including its full commit history and branches, on their own machine.
Unlike a 

**Centralized Version Control System (CVCS)** (such as SVN),
-----------------------------------------------------------
     which relies on a single central server to store all versioned files, DVCS removes the single point of failure.

### Advantages of DVCS over CVCS

**Offline Capability:** 
---------------------

    Because the entire history is stored locally, you can commit changes, view logs, create branches, and revert files without an internet connection.
 
**Faster Operations:** 
----------------------

    Most actions (like `git log`, `git diff`, and `git commit`) occur locally on your disk rather than over a network, making them nearly instantaneous.

**No Single Point of Failure:** 
--------------------------------

    If the central remote server crashes or becomes corrupted, any developer's local repository can be pushed back up to restore the project.

**Flexible Branching and Merging:** 
----------------------------------

    Developers can experiment in isolated local branches without affecting the main codebase or needing permission from a central server.

---

The Git Architecture & Workflow
=================================

Git tracks changes across four primary environments. Understanding how files move between these stages is essential for managing your code cleanly.

``text
+-------------------+     git add     +-------------------+    git commit    +-------------------+     git push     +-------------------+
|                   | --------------> |                   | ---------------> |                   | ---------------> |                   |
| Working Directory |                 |   Staging Area    |                  |    Local Repo     |                  |    Remote Repo    |
|  (Modified Files) | <-------------- |     (Index)       | <--------------- |     (.git/)       | <--------------- |  (GitHub/GitLab)  |
+-------------------+   git restore   +-------------------+   git rm --cached +-------------------+     git pull     +-------------------+


1.Working Directory: 
--------------------

    * The active folder on your computer where you create, edit, and delete files.

2.Staging Area (Index): 
-----------------------
    
    * A middle-ground buffer that holds snapshots of changes you intend to include in your next commit.

3.Local Repository:
-------------------

    * The hidden .git folder on your machine that permanently stores your committed history and snapshots.

4.Remote Repository: 
--------------------
    
   * A version of your repository hosted on a server (e.g., GitHub) used for backup and team collaboration.

Essential Git Commands
======================

   ==> git add

    * Moves modified or newly created files from the Working Directory to the Staging Area, preparing them to be committed.

Stage a specific file:
----------------------
   Ex===> git add index.html

Stage all modified and new files in the current directory:
--------------------------------------------------------

   => git add .

git commit
----------

    * It Takes everything currently in the Staging Area and saves it as a permanent snapshot in your Local Repository with a unique ID (hash) and descriptive message.

Commit staged changes with a message:
------------------------------------

Ex:==> git commit -m "Add navigation bar to homepage"

git restore
-----------

   * Discards uncommitted changes in your Working Directory (reverting a file back to its last committed state) or unstages files from the Staging Area.

Discard local edits in a file (revert to last commit):
-----------------------------------------------------

Ex:==> git restore index.html

Unstage a file (move it back from Staging Area to Working Directory without losing edits):
------------------------------------------------------------------------------------------

Ex:

    git restore --staged index.html
    git rm --cached

   * Removes a file from the Staging Area (and stops Git from tracking it in future commits) while keeping the actual file intact in your Working Directory. 
   * This is commonly used when you accidentally track a file that should be ignored (like .env or log files).

Untrack a file without deleting it from your computer:
-----------------------------------------------------

Ex:=>
    
    git rm --cached config.env
    git log

   * Displays the detailed commit history of the repository in reverse chronological order, showing the full commit hash, author, date, and commit message.

View full commit history:
-------------------------

    git log
    git log --oneline

   * A condensed version of git log that displays each commit on a single line, showing only the shortened 7-character commit hash and the commit title. 
   * Useful for quickly scanning project history.

View compact commit history:
----------------------------

    git log --oneline



