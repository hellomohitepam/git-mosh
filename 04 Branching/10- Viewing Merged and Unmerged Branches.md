# 10- Viewing Merged and Unmerged Branches

## List merge branches `--merged`

When we are finished working in a branch, we should merge it into ***`main`***, and afterwards delete new-feature pointer because they point to the same commit Main still holds all those commits.

To view the list of merged branches run the following command:

```zsh
git branch --merged
```

## List unmerged branches `--no-merged`

To view the list of unmerged branches run

```zsh
git branch --no-merged
```
