# 09- Renaming or Moving Files

When we rename a file and the run `git status` we will see the following output:

```zsh
❯ git status
On branch main

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	deleted:    02 Creating Snapshots/09- Renaming or Moving.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	02 Creating Snapshots/09- Renaming or Moving Files.md

no changes added to commit (use "git add" and/or "git commit -a")
```

We have changes, and both are unstaged. One is a delete operation (the old file), and the other is an untracked file (the new file name).

If we stage both files(separately) to the staging area and run git status one more time, Git is smart enough to detect that this was likely a rename operation:

```zsh
❯ git status
On branch main

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	renamed:    02 Creating Snapshots/09- Renaming or Moving.md -> 02 Creating Snapshots/09- Renaming or Moving Files.md
```

Git recognizes that we renamed the file and marks it as renamed. Like in the delete operation, there is a Git command to rename files:

Then we commit the changes:

```zsh
❯ git commit -m 'Rename file'
[main aec2762] Rename file
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename 02 Creating Snapshots/{09- Renaming or Moving Files.md => 09- Renaming or Moving.md} (100%)
```

If your intention was to rename the file and have Git track it as a single rename operation (which is generally better for history), the correct command would have been:

```zsh
git mv <current file> <new name>
```

