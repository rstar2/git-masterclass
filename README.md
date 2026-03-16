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

### After they have been committed

- Revert - `git revert [hash-commit]`
  > Undoes a previous commit by making a new commit on top of the history

- Reset - `git reset [hash-commit]`
  > Moves the head to a previous commit, e.g. "rewinds", this will discard/remove all next commits after this one
