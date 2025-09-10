---
# Git Cheat Sheet

## Key Concepts

- **Commit**: A snapshot of your codebase at a point in time.
- **Branch**: A reference to a commit; can have a tracked upstream.
- **Tag**: A reference (standard) or an object (annotated).
- **HEAD**: The current location in your working directory.

---

## 1. Git Configuration

```sh
git config --global user.name "Your Name"      # Set the name for commits and tags
git config --global user.email "you@example.com" # Set the email for commits and tags
git config --global color.ui auto                # Enable colorization of Git output
```

---

## 2. Starting a Project

```sh
git init [project name]      # Create a new local repository
git clone <project url>      # Download a project with full history
```

---

## 3. Day-to-Day Work

```sh
git status                  # Show status of working directory
git add [file]              # Add file(s) to staging area
git add .                   # Add all changed files
git diff [file]             # Show changes between working dir and staging area
git diff --staged [file]    # Show changes between staging area and repository
git checkout -- [file]      # Discard changes in working directory (unrecoverable)
git reset <path>            # Revert paths in index to their state in HEAD
git commit                  # Create a new commit from staged changes
```

---

## 4. Storing Your Work

```sh
git stash                   # Stash current changes for later use
git stash pop               # Apply and remove the latest stash
git stash drop              # Delete a specific stash
```

---

## 5. Branching Model

```sh
git branch [-a]             # List all local (and remote with -a) branches
git branch [branch_name]    # Create new branch from current HEAD
git checkout [-b] [branch_name] # Switch to or create and switch to branch
git merge [branch_name]     # Merge branch into current branch
git branch -d [branch_name] # Delete branch (if merged); -D to force
git rebase [branch_name]    # Rebase current branch onto [branch_name]
```

---

## 6. Inspecting History

```sh
git log [-n count]          # List commit history (limit to n commits)
git log --oneline --graph --decorate # Overview with labels and graph
git log ref                 # Commits on current branch not in ref
git log ..ref               # Commits on ref not in current branch
git reflog                  # List operations (checkouts, commits, etc.)
```

---

## 7. Tagging Commits

```sh
git tag                     # List all tags
git tag [name] [commit sha] # Create tag for current or specific commit
git tag -a [name] [commit sha] # Create annotated tag
git tag -d [name]           # Delete tag locally
```

---

## 8. Reverting Changes

```sh
git reset [--hard] [target] # Switch to target reference; --hard discards changes
git revert [commit sha]     # Create a new commit that reverts the specified commit
```

---

## 9. Synchronizing Repositories

```sh
git fetch [remote]          # Fetch changes from remote (no merge)
git fetch --prune [remote]  # Remove refs deleted from remote
git pull [remote]           # Fetch and merge changes from remote
git push [--tags] [remote]  # Push local changes/tags to remote
git push -u [remote] [branch] # Push branch and set upstream
```

---

## 10. Git Installation

- On Debian/Ubuntu:
	```sh
	sudo apt-get install git
	```
- Download from: [git-scm.com/downloads](https://git-scm.com/downloads)
- Free book: [Pro Git](https://git-scm.com/book)

---

## 11. Ignoring Files

Create a `.gitignore` file with patterns to ignore files/directories:

```gitignore
/logs/*
!logs/.gitkeep
/tmp
*.swp
```

This ignores all files in `logs/` (except `.gitkeep`), the `tmp/` directory, and all `*.swp` files.
git checkout -- [file] Discard changes in working directory. This operation is
unrecoverable.
git reset <path>...] Revert some paths in the index (or the whole index) to their
state in HEAD.
git commit Create a new commit from changes added to the staging area.
The commit must have a message!
2
11 Ignoring files
cat <EOF > .gitignore
/logs *
!logs/.gitkeep
/tmp
*.swp
EOF
To ignore files, create a .gitignore file in your repository with a line for each pattern. File ignoring will
work for the current and sub directories where .gitignore file is placed. In this example, all files are
ignored in the logs directory (excluding the .gitkeep file), whole tmp directory and all files *.swp.
10 Git installation
For GNU/Linux distributions, Git should be available in the standard system repository. For
example, in Debian/Ubuntu please type inthe terminal:
sudo apt-get install git
If you need to install Git from source, you can get it from git-scm.com/downloads.
An excellent Git course can be found in the great Pro Git book by Scott Chacon and Ben Straub.
The book is available online for free at git-scm.com/book.
09 Synchronizing repositories
git fetch [remote] Fetch changes from the remote, but not update tracking
branches.
git fetch --prune
[remote]
Delete remote Refs that were removed from the remote
repository.
git pull [remote] Fetch changes from the remote and merge current branch with
its upstream.
git push [--tags]
[remote] Push local changes to the remote. Use --tags to push tags.
git push -u [remote]
[branch]
Push local branch to remote repository. Set its copy as an
upstream.
06 Inspect history
git log [-n count] List commit history of current branch. -n count limits list to last
n commits.
git log --oneline
--graph --decorate
An overview with reference labels and history graph. One
commit per line.
git log ref . List commits that are present on the current branch and not
merged into ref. A ref can be a branch name or a tag name.
git log .ref List commit that are present on ref and not merged into current
branch.
git reflog List operations (e.g. checkouts or commits) made on local
repository.
07 Tagging commits
git tag List all tags.
git tag [name]
[commit sha]
Create a tag reference named name for current commit. Add
commit sha to tag a specific commit instead of current one.
git tag -a [name]
[commit sha] Create a tag object named name for current commit.
git tag -d [name] Remove a tag from local repository.
08 Reverting changes
git reset [--hard]
[target reference]
Switches the current branch to the target reference, leaving
a difference as an uncommitted change. When --hard is used,
all changes are discarded. It's easy to lose uncommitted
changes with --hard.
git revert [commit sha] Create a new commit, reverting changes from the specified
commit. It generates an inversion of changes. 