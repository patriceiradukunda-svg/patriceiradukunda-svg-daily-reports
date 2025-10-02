````markdown
# patriceiradukunda-svg-day04-report.md

## Course: Introduction to the Python Programming Language  
**Student:** Patrice IRADUKUNDA  
**Program:** Master’s Student — Mathematical Science (Regular)  
**Date:** Friday, September 26, 2025

---

## One-line Summary
Today’s lesson introduced **version control with Git** using **Git Bash**. We created and managed a local Git repository, learned how to add/commit files, handled deletions and restorations, examined commit history, and practiced safe workflows and troubleshooting (index lock files, CRLF warnings, and push/pull issues). We did **all work locally** and did not push to GitHub during the session.

---

# Detailed narrative (chronological)

### 1. Lecturer’s opening, context, and success tips
The lecturer began by introducing himself and the high-level objectives of the course. He stressed that version control is an essential skill for programmers, researchers, and students working on collaborative projects. He provided practical tips on how to approach learning Git and programming in general:

- Practice regularly and commit small incremental changes rather than large monolithic changes.  
- Write descriptive commit messages so the history tells a meaningful story (e.g., `Add day04 notebook; fix formatting`).  
- Use branches for work-in-progress to avoid destabilizing the main branch.  
- Keep backups and push to a remote (GitHub) once comfortable with local workflows.  
- Don’t be afraid to make mistakes in Git — most mistakes are recoverable.

He emphasized that today’s focus would be local repository management: we would initialize repositories, create and organize files/folders, learn to stage and commit, and practice delete/restore — all on the machine using **Git Bash**.

---

### 2. Environment & preparation
Before starting, the lecturer confirmed that everyone had:

- Git and Git Bash installed (we used Git Bash on Windows).  
- A working project folder where we would run commands (the instructor recommended keeping projects under `OneDrive` or a personal folder).  
- Basic familiarity with command line navigation (`pwd`, `ls`, `cd`) since Git Bash was the environment for the lab.

We opened Git Bash inside our project folder: `OneDrive/Daily-Report---Python-Programming`.

Sample commands used at the beginning (context only):
```bash
pwd        # print working directory
ls -la     # list files and show hidden .git if present
````

---

### 3. Initialize a local repository

The first hands-on step was to initialize a Git repository in the project folder.

Commands executed:

```bash
git init
# optionally ensure main is used as branch name
git branch -M main
```

**What this does:**

* `git init` creates a hidden `.git` directory which stores all Git metadata and history.
* `git branch -M main` renames the current branch to `main` (useful on systems that default to `master` or to ensure consistency).

**Instructor note:** At this stage the folder is now under version control, but nothing is committed yet.

---

### 4. Create files and initial staging

We created example files to practice with. Typical files used in the lab were: `README.md`, `patrice_iradukunda_report_day00.txt`, and new daily report templates (e.g., `day1.txt` which we later deleted as part of an exercise).

To check repository state and untracked files:

```bash
git status
```

To stage files for commit:

```bash
git add -A
# or stage specific files
git add README.md patrice_iradukunda_report_day00.txt
```

**Why use `git add -A`?**
`-A` stages all changes: additions, modifications, and deletions. It is a convenient way to stage everything when you are ready to commit the current working set.

---

### 5. Commit to create a snapshot

Once files were staged we created a commit to save the local snapshot. We practiced writing meaningful commit messages.

Examples from class:

```bash
git commit -m "Initial commit — add README and day00 report"
```

**Instructor tips for commit messages:**

* Keep the subject line concise (50 characters or less is a common recommendation).
* If necessary, add a blank line and a longer description explaining the why (not required for small commits).
* Use imperative verbs: `Add`, `Fix`, `Remove`, `Update`.

---

### 6. Inspecting history and status

We verified commits and repository status frequently.

Useful commands:

```bash
git status
git log --oneline
# or for more detail
git log --stat --decorate --graph --all
```

`git status` shows staged/un-staged/untracked files and tells if branch is ahead/behind remote (if remote configured).
`git log --oneline` gives a condensed commit history.

---

### 7. Practicing file deletion and restoration (core exercise)

A central exercise during the lab was intentionally deleting a file to practice Git’s ability to track and restore changes.

**Scenario:** We deleted `day1.txt` from the working folder (simulating accidental deletion).
`git status` then reported:

```
deleted:    day1.txt
```

**Options practiced:**

**A — Commit the deletion (record that file is removed):**

```bash
# stage deletions and other changes
git add -A
# or explicitly
git rm day1.txt
# commit the deletion
git commit -m "Remove day1.txt — obsolete"
```

This records the removal in history; file is removed from working directory and commit.

**B — Restore the deleted file from last commit (undo the accidental deletion):**

```bash
git restore day1.txt
# older versions of Git might use
# git checkout -- day1.txt
```

`git restore` brings the file back from the HEAD commit into the working directory.

We practiced both workflows to understand when to choose each: commit deletion when files are intentionally removed; restore when deletion was a mistake.

**Cause:** A previous Git command was interrupted or another git process (editor/git gui) is using the repository.
**Resolution steps:**

1. Ensure no other Git processes are running (close editors/IDEs).
2. If safe, remove the lock file manually:
#### b) Line ending warning: `LF will be replaced by CRLF`

**Message shown on Windows:**

```
warning: LF will be replaced by CRLF in <file>.
```

**Cause:** Different operating systems use different line endings. Windows uses CRLF while Unix/Linux uses LF. Git can be configured to automatically convert line endings.
**Recommended fix/config:**

```bash
git config --global core.autocrlf true
```

This makes Git convert LF to CRLF on checkout on Windows while storing LF in the repository.

#### c) Push rejected — remote contains work you do not have locally

**Error shown:**

```
! [rejected] main -> main (fetch first)
error: failed to push some refs to 'https://github.com/...'

```bash
git push origin main
```

Instructor emphasized: both are **conventions**, not forced names — but they are widely used and recommended for clarity.

---

### 10. Brief mention: pushing to GitHub (not performed)

The lecturer walked us through the steps needed to connect to GitHub (DEMONSTRATION only — no push executed):

```bash
# add remote (example)
git remote add origin https://github.com/yourusername/Daily-Report---Python-Programming.git
# push and set upstream
git push -u origin main
```

We were instructed to delay pushing until we are comfortable with local workflows. The instructor also explained access rights and authentication methods (HTTPS with token or SSH keys) but we did not configure or run them in class.

---

### 11. Class exercises (what each student was asked to do)

1. Initialize a git repository in your project folder.
2. Create `README.md` and at least one day-report file (e.g., `patrice_iradukunda_report_day00.txt`).
3. Stage and commit those changes with a clear message.
4. Delete `day1.txt` to simulate an accidental deletion and then practice restoring it.
5. Force an index.lock situation (or simulate by interrupting a git command) and practice safe removal.
6. Practice reading `git status` and `git log` after each step and document the outputs in your notes.

Students were encouraged to keep their lab notebook updated with the commands and outputs. The instructor used the notebook file `PyPro-SCiDaS-day_04_version_control_with_git_local.ipynb` as the class transcript and suggested we save our own copy.

---

## Artifacts created during the session

* `README.md` — starter project description (skeleton).
* `patrice_iradukunda_report_day00.txt` — initial day 0 report.
* Temporary files and examples used for practicing `git add`, `git commit`, `git restore`.

---

## Full list of useful commands covered (reference)

```bash
# environment
pwd
ls -la

# initialize repo
git init
git branch -M main

# inspect
git status
git log --oneline

# stage & commit
git add -A
git add <file1> <file2>
git commit -m "Descriptive message"

# delete & restore
rm day1.txt         # delete from filesystem (bash)
git status          # shows deleted: day1.txt
git restore day1.txt    # restore from HEAD
# or commit deletion
git rm day1.txt
git add -A
git commit -m "Remove day1.txt"

# troubleshooting
rm -f .git/index.lock   # remove lock file if safe
git config --global core.autocrlf true  # line ending handling

 remote (demonstrated but not executed by students)
git remote add origin <url>
git push -u origin main
git pull origin main --rebase

# rebase rescue
# after resolving conflicts
git rebase --continue

# stash as alternative to commit
git stash
git stash apply
```

---

## Best practices & instructor recommendations (summarized)

* Commit frequently and with small, focused changes.
* Use meaningful commit messages.
* Run `git status` often — it’s a quick safety check.
* Keep `main` stable; do experimental work in feature branches.
* Learn how to resolve simple merge/rebase conflicts — practice helps.
* Push to a remote (GitHub) regularly once comfortable; configure SSH keys or a token for authentication.

---

## Next steps and personal plan

1. Connect this local repository to a GitHub repository and push the current commits.
2. Practice creating branches locally and performing merges (feature branch → main).
3. Learn to use `.gitignore` to avoid committing temporary or sensitive files (e.g., `__pycache__/`, `.env`).
4. Review the class notebook (`PyPro-SCiDaS-day_04_version_control_with_git_local.ipynb`) and copy the example commands into my own lab notebook for future reference.
5. Collaborate with a classmate to practice push/pull workflows and resolve real merge conflicts.

---

## Personal Reflection (detailed)

Attending today’s lab gave me concrete confidence that Git is not an intimidating black box. The step-by-step exercises — initialize, stage, commit, delete, and restore — illustrated Git’s core strengths: a compact history of changes, the ability to undo mistakes, and a reliable mechanism for tracking progress. Encountering real issues (index lock, CRLF warnings, and push rejections) in a controlled classroom setting helped me understand not only commands but also the why and the recovery steps. I feel prepared to proceed to the next stage: connecting to GitHub and beginning collaborative workflows.

---

**Prepared by:** Patrice IRADUKUNDA
**File:** `patriceiradukunda-svg-day04-report.md`
**Course:** Introduction to the Python Programming Language
**Date:** Friday, September 26, 2025

```
```

**Instructor note:** We practiced this conceptually; pushing to GitHub was not executed in class.

#### d) Typo in commit or push commands

Small typos cause confusing errors (e.g., `git commit m- "msg"` or `git push orgin main`). We practiced reading errors carefully and correcting typos (`-m` vs `m-`, `origin` vs `orgin`).

---
* **`main`**: a branch name (the default primary branch in modern Git setups). Historically `master` was used; newer repositories use `main` by default.

### 9. Discussion: `origin` & `main` — conventions vs hard requirements

We discussed what `origin` and `main` represent:

* **`origin`**: a conventional name for the remote repository. When you clone a repository, Git creates a remote named `origin` pointing to the clone source. You can name remotes anything.
hint: Updates were rejected because the remote contains work that you do
hint: not have locally...
```
git pull origin main --rebase
# handle any rebase conflicts (edit files to resolve), then
git rebase --continue
```

3. Push after rebase completes:


```bash
**Cause:** The remote repository has commits not present locally. Git prevents push to avoid losing remote changes.

2. Pull remote changes with rebase to replay local commits on top:
**Safe resolution (class workflow):**

1. Commit or stash local changes:

```bash
git add -A
git commit -m "WIP: save local changes"
# or stash: git stash
```

```bash

rm -f .git/index.lock
```

3. Retry `git add` / `git commit`.

**Instructor note:** Always check that no process is actually running before removing the lock file. Removing it while another Git process runs can corrupt state.

