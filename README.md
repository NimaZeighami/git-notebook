# my-git-notebook
I want to write down everything I’ve learned about Git here.

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
