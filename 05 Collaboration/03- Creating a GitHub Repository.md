# Git & GitHub: Creating and Connecting Repositories

This guide covers the two main ways to start a project: starting from scratch locally or starting with an existing GitHub repository.

---

# Method 1: The "New Project" (Local First)
*Use this if you already have code on your computer and want to push it to a new GitHub repo.*

## 1. Initialize Local Repository
In your project folder, run:
```bash
git init
git add .
git commit -m "Initial commit"
```

## 2. Create the Repo on GitHub

Go to github.com/new.

Name your repository (do not initialize with a README/License if you have local code).

Click Create repository.

## 3. Link Local to Remote
Copy the URL of your new GitHub repo and run:
Add the remote link and name it 'origin'
`git remote add origin [https://github.com/USER_NAME/REPO_NAME.git](https://github.com/USER_NAME/REPO_NAME.git)`

| Word | Meaning |
|---|---|
| `git` | the git tool |
| `remote` | we are working with remote repositories |
| `add` | we want to add a new remote connection |
| `origin` | the nickname/alias we are giving to this remote |
| `<url>` | the actual address of the remote repository |

## You can have multiple remotes:
```
git remote add origin https://github.com/username/myproject.git
git remote add upstream https://github.com/original/myproject.git
git remote add gitlab https://gitlab.com/username/myproject.git
```
> Each remote has its own nickname pointing to a different URL.

## Useful remote commands:
```
git remote -v              # list all remotes and their URLs
git remote remove origin   # remove a remote
git remote rename origin upstream   # rename a remote
git remote set-url origin <new-url> # change the URL of a remote
```

Rename your local default branch to 'main' (if it's named 'master')
`git branch -M main`

Push your code and set 'origin/main' as the tracking reference
`git push -u origin main`
> The -u flag sets up tracking — it tells Git:
> "whenever I am on main branch and type git push, automatically push to origin/main"


# Method 2: The "Clone" (GitHub First)
Use this if you created the repository on GitHub first (with a README or License) and want to bring it to your computer.

1. Copy the URL
On the GitHub repository page, click the green Code button and copy the HTTPS or SSH URL.

2. Clone to Local Machine
`git clone [https://github.com/USER_NAME/REPO_NAME.git](https://github.com/USER_NAME/REPO_NAME.git)`
> Or when you clone a repo Tracking is automatically set up — so git push just works without any extra configuration.

3. Note: This automatically sets up the remote named origin and creates the origin/main tracking branch for you.
