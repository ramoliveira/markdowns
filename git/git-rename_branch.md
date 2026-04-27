# Rename Local and Remote Branch

## 1. Rename Local Branch
You can rename the branch regardless of wheter you are currently on it or not.
- **If you are on the branch:**
  ```shell
  git branch -m <new-name>
  ```
- **If you are on a different branch:**
  ```shell
  git branch -m <old-name> <new-name>
  ```
*Note: Use `-M` instead of `-m` if you want to force the rename even if the new branch name already exists.*

## 2. Update the Remote Branch
After renaming locally, follow these steps to reflect the change on the remote repository (e.g., GitHub, GitLab, or Bitbucket).

  1. **Push the new branch and set it as upstream:**
     ```shell
     git push origin -u <new-name>
     ```
     *This creates the new branch on the remote and links it to your local branch.*
  2. **Delete the old branch from the remote:**
     ```shell
     git push origin --delete <old-name>
     ```

## TLDR;
```shell
git branch -m <new-name>
git push origin -u <new-name>
git push origin --delete <old-name>
```

Made by Gemini, Edited by Me
