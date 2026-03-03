# 06- Fetching

The **Local Repository** and **Remote Repository** work independently. If we have new commits in our **Remote Repository**, because another team member pushed is work, our **Local Repository** will not be aware of it.

We have to use the `git fetch <remote-repository>` command to download the new commits. When we do so the **_`origin/main`_** pointer will move forward, and point to the new commits. But our working directory will not be updated

```zsh
git fetch origin
```
```
              D   (your commit)
             /
A --- B --- C
             \
              E   (teammate commit)
```

| Pointer       | Points To |
| ------------- | --------- |
| `main`        | D         |
| `origin/main` | E         |
| `HEAD`        | D         |

## ✅ Option 1: Merge (Safe & Simple)
```git merge origin/main```

```
A --- B --- C --- D
             \      \
              E ----- M
                     ↑
                   main
```

git push

## ✅ Option 2: Rebase (Cleaner History)

```
git rebase origin/main
```
> Git moves your commit D on top of E.

```A --- B --- C --- E --- D'
                          ↑
                        main
```

git push 

## 🧠 Simple Rule
### If someone pushed before you:
1. git fetch
2. git rebase origin/main (or merge)
3. git push

Optionally we can specify a branch to the `fetch` command, like `git fetch <remote-repository> <branch-name>`.

```zsh
git fetch origin bugfix
```

### So locally you have remote-tracking branches:
- origin/main
- origin/dev
- origin/feature-login
### 👥 Now Team Makes Changes
- main           → new commit M1
- dev            → new commit D1
- feature-login  → new commit F1
> To update our branch with the changes downloaded from the `fetch` command, we have to merge them with our branch, with the command:

# 📊 Comparison Table

| Command                 | What It Fetches                  | Updates Which Remote-Tracking Branches |
| ----------------------- | -------------------------------- | -------------------------------------- |
| `git fetch`             | All branches from default remote | All `origin/*` branches                |
| `git fetch origin`      | All branches from `origin`       | All `origin/*` branches                |
| `git fetch origin main` | Only `main` branch               | Only `origin/main`                     |

🧩 What Happens During git fetch
- New commit objects downloaded
- Stored in .git/objects
- origin/main file updated

```zsh
git merge origin/master
```

## Remote and Local branches

With the command `git branch -vv` we can se how the remote and local branches are diverging.

```zsh
❯ git branch -vv
* main bbe3812 [origin/main: ahead 2] add details to lesson
```

In the above output from the `git branch -vv` we can see that our local **_`main`_** branch is connect to the remote **_`origin/main`_** branch. And the local branch is ahead by 2 commits.
