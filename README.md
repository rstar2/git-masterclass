# 🚀 Git & GitHub Masterclass

## Untrack files

- `git rm --cached [file]`
  > Untrack the file but keep it in the working directory (this is what `--cached` flag does, otherwise it will also delete it from the working directory)

## Undoing Changes

### Before they are staged

- `git restore [file]`
  > Discard the changed file in working directory as it was before

- `git checkout [file]`
  > ...  

### After they are staged

- `git restore --staged [file]`
  > Unstages the staged file and keeps the changes in the working tree

- `git restore --staged --worktree [file]`
  > Will unstage and discard changes in the working directory

- Historically before Git 2.23 `git checkout [file]` could be used for same thing, but the `checkout` command was used for many different things, so now the `restore` is much more clear and explicit

### After they have been committed

- Revert - `git revert [hash-commit]`
  > Undoes a previous commit by making a new commit on top of the history

- Reset - `git reset [hash-commit]`
  > Moves the head to a previous commit, e.g. "rewinds", this will discard/remove all next commits after this one

## Merging branches

`git merge feature`

- Fast-forward Merge
  > When there are not commits in the "main" branch (the branch where the merge happens). Result is a clean and linear Git history. It happens automatically if that is the case
- Three-Way (True) Merge (Merge commit) - Occurs when both branches have new commits since they diverged. Git creates a `merge commit` combining both histories:
- Squash merge - some people may prefer it. Squashes all commits from the "feature" branch and adds them as one in "main" - `git merge --squash feature`. Mainly for PR workflows.
This merge also don't commit the "squashed" feature changes, just stages one changes as one, but `git commit -m "...."` has to be explicitly run in order the commit to be applyed to "main"

## Stashing

- Stashing makes sense when switching branching while there are changes in the working directory or the index. Or when pulling from an remote branch.
- Put a temp "change" in the stash stack and "clearing" the working tree `git stash push` and `git stash pop` - this will add all changed files from the working directory AND the stage index, it does **NOT** add to the stash new untracked by Git files.
  > To add also the untracked files `git stash push -u`.
- Multiple stashes
  `git stash push -m "message 1"` , `git stash push -m "message 2"`, ...
  Now stashes can be listed with `git stash list` and then pop the desired one like `git stash pop stash@{1}`
- A stash entry can also be applied and still left in the stash with `git stash apply ....`

## Commit goodies

- `git commit --amend` - This will amend the latest commit with the new changes
- `git commit -a -m "message"` or just `git commit -am "message"` - shortcut for `git add .` plus `git commit -m "message"`