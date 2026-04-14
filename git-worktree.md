# Git worktree

A **Git worktree** allows you to have multiple branches of the same repository checked out simultaneously in different directories. This is an efficient alternative to `git stash` or cloning a repository multiple times when you need to switch context quickly, sush as fixing a critical bug while in the middle of a feature.

## 1. Creating a Worktree
To add a new worktree, use the `git worktree add` command. This creates a new directory and checks out a branch into it.

- ### Create a new branch:
  To add a new worktree, use the `git worktree add <path> -b <new-branch-name>`.
  *Example:* `git worktree add ../hotfix -b hotfix/bug-001`
- ### Check out an existing branch in a new directory:
  `git worktree add <path> <existing-branch-name>`
  *Example:* `git worktree add ../app-feature-x feature/x`

## 2. Managing Worktrees

- **List all active worktrees:**
  `git worktree list` displays the path, current commit hash, and branch for each worktree.
  
- **Remove a worktree:**
  When finished, use `git worktree remove <path>`.
  *Note:* If you have uncommited changes, Git will prevent removal unless you use the `--force` (or `-f`) flag.

- **Move or repair:**
  Use `git worktree move <old-path> <new-path>` to relocate one, or `git worktree repair` if you manually moved directories and broke the links.

## 3. Key Rules & Tips

- **No Simultaneous Checkout:** You cannot check out the same branch in two different worktrees at the same time.
- **Shared Metadata:** All worktrees share the same `.git` history and object database, meaning a `git fetch` in one worktree updates the others.
- **Directory Placement:** It is often best to create worktrees one level *above* your current directory (using: `../`) to avoid nesting them inside your main project folder.
- **Bare Repositories:** Advanced users often clone a repository as "bare" (`git clone --bare`) and then use worktrees for all active development to keep the main directory organized.

Made by Gemini, Edited by Me
