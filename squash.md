# Squashing Commits

Squashing commits with `git rebase` allows you to combine multiple small commits into a single, 
clean commit to maintain a linear and readable project history.

## Step-by-Step Guide to Squashing

1. **Identify the Commits:** Determine how many commits you want to combine. Run `git log --oneline`
to see your recent history.

2. **Start Interactive Rebase:** Run the following command, replacing `n` with the number of commits
to squash:

    ```bash
    git rebase -i HEAD~n
    ```

    Alternatively, use the hash of the commit before those you want to modify: `git rebase -i <commit-hash>`.

3. **Choose Actions in the Editor:** Your default text editor (often Vim) will open with a list of commits.

    1. Leave the **first (top)** commit as `pick`.
    2. Change `pick` to `squash` (or just `s`) for all subsequent commits you want to merge into the first one.
    3. *Tip*: Use `fixup` (of `f`) instead of `squash` if you want to discard that commit's message entirely.

4. **Finalize the Commit Message:** After saving and closing the first editor, a second window will open.
Combine or rewrite the commit messages into one concise summary.

5. **Push Changes:** Since you have rewritten history, you must use a force push to update the remote branch:

    ```bash
    git push --force-with-lease
    ```
    The `--force-with-lease` flag is safer than a standard force push as it prevents overwriting other's work.

## Best Practices

- **Never rebase shared branches:** Only squash commits on your local, private feature branch before merging into
  a main or shared branch to avoid disrupting collaborators.
- **Backup**: Create a temporary backup branch (`git branch backup-branch`) before starting a complex rebase in
  case you need to revert.
- **Auto-Squashing:** For frequent "fixup" commits, use `git commit --fixup <hash>` and then `git rebase-i --autosquash`
  to automate selection process. 

Made by Gemini, Edited by Me

## TLDR;

|Command|Description|
|:-|:-|
|`git branch backup-<branch>`|Create a temporary backup branch.|
|`git log --oneline`|Checks which commit to pick, squash, or fixup.|
|`git rebase -i HEAD~n`|Starts interactive rebase for the last `n` commits.|
|`pick` to `squash`|Leave the **first** commit as `pick`, subsequent as `squash`.|
|`git push --force-with-lease`|To rewritte history.|

Made by Me

