# Nima'Z Git Notebook
I want to write down everything I’ve learned about Git here.


# Introduction


### What is Version Control?

A **Version Control System (VCS)** is a tool that acts as a **time machine for your projects**. It systematically records all changes to a set of files over time. This allows you to revisit any previous "snapshot" (called a **commit**) of your project at any time.

### Why Do We Need Them?

We need VCS for three core reasons:

1.  **Safety & Recovery:** It is your ultimate undo button. If you make a mistake, break something, or lose files, you can easily revert to a previous, working state. You never lose your work.
2.  **History & Accountability:** It tracks **who** made a change, **when**, and **why** (via commit messages). This is invaluable for finding when a bug was introduced and understanding the project's evolution.
3.  **Collaboration:** It allows multiple people to work on the same project simultaneously without overwriting each other's work. It provides tools to merge everyone's contributions together cleanly.

### How Do They Generally Work?

VCSs work by managing different levels of history:

1.  **Local VCS (e.g., RCS):** The simplest form. It keeps a database of changes (as patches) on your **local machine**. It's better than manually copying folders but doesn't allow for collaboration.
2.  **Centralized VCS (CVCS) (e.g., Subversion, CVS):** There is a **single, central server** that stores all the files and their history. Everyone **checks out** files from this server. This allows collaboration but creates a single point of failure—if the server dies, you lose the entire project history unless you have backups.
3.  **Distributed VCS (DVCS) (e.g., Git, Mercurial):** This is the modern standard. Instead of just checking out files, every developer **clones** the entire repository, including its **complete history**. This means every single working copy is a full backup. This allows for more flexible workflows and has no single point of failure.

### What Are the Alternatives to Git?

Git is a **Distributed VCS (DVCS)**. Its main alternatives are:

*   **Centralized (CVCS) Alternatives:**
    *   **Apache Subversion (SVN):** A very popular, centralized system. Users "check out" files from a central server.
    *   **Perforce (Helix Core):** Used often in large-scale enterprise environments and game development (e.g., for versioning large binary files like art assets).
    *   **Concurrent Versions System (CVS):** One of the earliest systems, now largely obsolete.

*   **Distributed (DVCS) Alternatives:**
    *   **Mercurial (Hg):** A contemporary of Git that is very similar in goals and capability but often considered simpler and cleaner to use. It never achieved the same massive adoption as Git.
    *   **Bazaar (Bzr):** Another distributed system, sponsored by Canonical for a time.

**In summary:** Git won the DVCS war due to its speed, robust functionality, and the network effect of platforms like GitHub. Today, **Git is the de facto standard** for version control, especially in software development. The main "alternatives" in use today are other types of systems like **Subversion** (which is centralized) or **Mercurial** (which is distributed but less common).


# Basics


## GIT AREAS
Git has 4 main areas :
1.  **Working Directory:** Our actual files of projects. We create and edit files here.
2.  **Staging Area (Index):** A prep area where we add (`git add`) changes we want to include in the next commit. It's our "shopping cart."
3.  **Local Repository (.git folder):** Where Git permanently stores our commits as snapshots. We save from the staging area here with `git commit`.
4.  **Remote Repository (origin):** The shared repository on a server like GitHub or GitLab. We share our commits here with `git push`.





## GIT COMMANDS (IN ORDER OF USE)


**GIT INIT**
*   **WHAT IT DOES:** Initializes a new Git repository in the current directory. Creates a hidden `.git` folder that tracks all changes.
*   **WHEN TO USE:** Once per project, when you are starting version control for a new codebase that isn't already a Git repo.
*   **CRUCIAL NOTE:** **Without running this command first, no other Git commands are available** in that directory. It creates the necessary infrastructure for Git to work.
*   **EXAMPLE:** `git init`

---

**GIT CLONE**
*   **WHAT IT DOES:** Downloads an entire existing repository from a remote server (like GitHub) to your local machine. It automatically runs `git init`, adds the remote (`origin`), and checks out the code.
*   **WHEN TO USE:** When you want to get a local copy of a project you want to contribute to or work on.
*   **EXAMPLE:** `git clone https://github.com/user/repo.git`

---

**GIT STATUS**
*   **WHAT IT DOES:** Your most important command. Shows the current state of your working directory and staging area. It displays which files are modified, untracked, or staged for commit. It also shows if your branch is ahead/behind the remote.
*   **WHEN TO USE:** Constantly. **Before and after every other command** to understand your current situation. Especially at the start of a work session and before `git add`.
*   **EXAMPLE:** `git status`

---

**GIT ADD**
*   **WHAT IT DOES:** Adds changes from the working directory to the staging area. This tells Git which changes you want to include in your next commit. For new files, it also tells Git to start tracking them.
*   **WHEN TO USE:** After making changes to files you want to save in the next commit.
*   **EXAMPLE:**
    *   Stage a specific file: `git add filename.txt`
    *   Stage all changes: `git add .`

---

**GIT COMMIT**
*   **WHAT IT DOES:** Takes everything in the staging area and creates a permanent snapshot (commit) of it in the local repository.
*   **WHEN TO USE:** After you have used `git add` and are ready to permanently save a set of changes.
*   **EXAMPLE:** `git commit -m "Describe the changes made in this commit"`

---

**GIT PUSH**
*   **WHAT IT DOES:** Uploads your local commits to the remote repository (e.g., GitHub). This shares your work with others.
*   **WHEN TO USE:** After you have committed your changes and are ready to share them with the team or back them up online.
*   **EXAMPLE:** `git push origin main`

---

**GIT PULL**
*   **WHAT IT DOES:** = `GIT FETCH` + `GIT MERGE`. Fetches the latest changes from the remote repository and immediately merges them into your current local branch.
*   **WHEN TO USE:** **At the beginning of every work session** to ensure you are starting with the latest code from your team.
*   **EXAMPLE:** `git pull origin main`

---

**GIT FETCH**
*   **WHAT IT DOES:** Downloads the latest changes (new commits, branches) from the remote repository but does NOT merge them into your local branches. It updates your remote-tracking branches (e.g., `origin/main`).
*   **WHEN TO USE:** When you want to see what others have been working on without merging their changes into your own work yet. A safe way to check for updates.
*   **EXAMPLE:** `git fetch origin`

---

**GIT CHECKOUT**
*   **WHAT IT DOES:** Switches to a different branch or restores files in your working directory to a previous state.
*   **WHEN TO USE:**
    1.  To switch branches: `git checkout branch-name`
    2.  To create and switch to a new branch: `git checkout -b new-branch-name`
*   **EXAMPLE:** `git checkout develop`
