# Git & Diff Cheat Sheet

## Table of Contents

- [The Diff Command](#the-diff-command)
- [Git Configuration](#git-configuration)
- [Getting Started](#getting-started)
- [Prepare to Commit](#prepare-to-commit)
- [Make Commits](#make-commits)
- [Code Archaeology](#code-archaeology)
- [Diff Staged/Unstaged Changes](#diff-stagedunstaged-changes)
- [Diff Commits](#diff-commits)
- [Discard & Undo Changes](#discard--undo-changes)

## The Diff Command

Comparing files and directories via the command line (pre-Git).

```bash
# Basic file comparison
diff file1.txt file2.txt

# Unified format (commonly used in software dev)
diff -u file1.txt file2.txt

# Create a patch file (redirect output to a file)
diff -u original.txt modified.txt > changes.patch

# Apply a patch to the original file
patch original.txt < changes.patch
```

## Git Configuration

Setting up the environment and identity.

```bash
# Set global username and email
git config --global user.name "Your Name"
git config --global user.email "email@example.com"

# Check configuration
git config --list
```

## Getting Started

```bash
# Initialize a new repository
git init
```

```bash
# Clone an existing repository
git clone <url>
```

## Prepare to Commit

```bash
# Check the status of your files (Vital command!)
git status
```

```bash
# Check what you added
git add <file>

# Add all untracked files and unstaged changes
git add .

# Choose which parts of a file to stage
git add -p
```

```bash
# Move file
# (stages the move automatically)
git mv <old> <new>
```

```bash
# Delete file
# (stages the deletion automatically)
git rm <file>

# Stop tracking file but keep it in local file system
git rm --cached <file>
```

## Make Commits

```bash
# Make a commit (open text editor for message)
git commit

# Make a commit
git commit -m 'message'

# Commit all unstaged changes (modified files)
git commit -am 'message'
```

```bash
# Modify the last commit
# (change message or add forgotten files)
git commit --amend


# Scenario A: Typo in the commit message.
# 1. You commit with a typo
git commit -m "Addd new feature"
# 2. You fix the message
git commit --amend -m "Add new feature"
# Result: The history only shows ONE perfect commit.

# Scenario B: You forgot to add a file.
# 1. You commit, but forget 'style.css'
git commit -m "Update homepage"
# 2. You realize you forgot the file
git add style.css
# 3. You amend the previous commit
git commit --amend --no-edit
# Result: The previous commit now includes 'style.css'.
# '--no-edit': "keep the old commit message".
```

**⚠️ CRITICAL WARNING:** Never use `--amend` on commits you have already **pushed** to a shared repository (like GitHub). Amending changes the **Commit ID (Hash)**. If others have downloaded the old commit, and you force a new "amended" version, it will break their history. Only amend commits that exist purely on your local machine.

## Code Archaeology

```bash
# Look at a branch's history
git log main [-<number of logs> | -p (for diff)]
git log --graph main
git log --oneline
```

```bash
# Show every commit that modified a file
git log <file>
```

```bash
# Show who changed what and when in a file
git blame <file>
```

## Diff Staged/Unstaged Changes

```bash
# Diff all staged and unstaged changes vs HEAD
git diff HEAD
```

```bash
# Diff just staged changes
# (what will be committed)
git diff --staged
```

```bash
# Diff just unstaged changes
# (what is in working dir)
git diff
```

## Diff Commits

```bash
# Show diff between a commit and its parent
git show <commit>
```

```bash
# Diff two commits
git diff <commit_A> <commit_B>
```

```bash
# Diff one file since a specific commit
git diff <commit> <file>
```

```bash
# Show a summary of a diff
# (file names and change counts)
git diff <commit> --stat
```

## Discard & Undo Changes

Using the modern restore command for file operations.

```bash
# 1. Unstage a file
# Move from Staging -> Working Directory
# Use this if you 'git add'ed something by mistake.
git restore --staged <file>
```

```bash
# 2. Discard local changes
# Overwrite Working Directory -> HEAD
# DANGEROUS: You will lose your work in this file.
git restore <file>
```

```bash
# 3. Undo the last commit but keep changes in files
git reset --soft HEAD~1
```

```bash
# 4. Undo the last commit and DESTROY changes
git reset --hard HEAD~1
```

```bash
# 5. Create a commit to undo the last commit
git revert HEAD
# OR
git revert <Commit ID>
```

## Branching and Merging

Managing parallel lines of development.

```bash
# List branches
git branch

# Create a new branch
git branch <branch-name>

# Switch to a branch
git checkout <branch-name>
# or
git switch <branch-name>

# Merge a branch into the current branch
git merge <branch-name>

```

## Remote Repositories

Collaborating with others (GitHub, GitLab, etc.).

```bash
# View remote repositories
git remote -v

# Add a remote
git remote add origin <url>

# Push changes to remote
git push origin <branch-name>

# Pull changes from remote
git pull origin <branch-name>

```

## References

- Git Official Documentation
- Pro Git Book
- GitHub Cheat Sheet
