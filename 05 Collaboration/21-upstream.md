# What is an "upstream"?
- In Git, upstream refers to a tracking relationship between a local branch and a remote branch.
- When a local branch has an upstream set, Git can automatically know where to push to and pull from — without you specifying it every time.

# Think of it like a local copy linked to a remote original:
```
Local repo                     Remote repo (origin)
──────────────────             ──────────────────────
main          ──tracks──▶      origin/main
feature/login ──tracks──▶      origin/feature/login
hotfix        ──(no upstream)
```
# How upstream gets set
1. When you clone a repo Git automatically sets main (or master) to track origin/main.
2. When you push with -u `git push -u origin feature/login` # -u is short for --set-upstream`
> After this, plain git push and git pull just work.

# Manually with git branch --set-upstream-to
```
git branch --set-upstream-to=origin/feature/login feature/login
# or, if you're already on the branch:
git branch --set-upstream-to=origin/feature/login
```
- Git immediately validates that the target (origin/feature/login) actually exists in your local remote-tracking refs. If it doesn't, it refuses.
-  use git push -u instead, which creates the remote branch AND sets the upstream in one shot: `git push -u origin feature/login`

# When you git checkout a remote branch
## if `origin/feature/login` exists:
1. Creates a local branch `feature/login`
2. **Automatically sets** `origin/feature/login` as its upstream
## else
- **git checkout feature/login simply fails**
- To create a new local branch that doesn't exist anywhere: `git checkout -b feature/login`

# Inspecting upstreams
```
# See all branches + their upstreams
git branch -vv

# Output looks like:
# * main          a1b2c3d [origin/main] Latest commit message
#   feature/login d4e5f6a [origin/feature/login: ahead 2] My feature
#   hotfix        7g8h9i0 (no upstream shown)
```
# What upstream enables
## Once set, these shortcuts all work:
| Action                 | Without Upstream            | With Upstream        |
| ---------------------- | --------------------------- | -------------------- |
| **Push**               | `git push origin main`      | `git push`           |
| **Pull**               | `git pull origin main`      | `git pull`           |
| **See diff vs remote** | `git diff origin/main`      | `git diff @{u}`      |
| **See log vs remote**  | `git log origin/main..HEAD` | `git log @{u}..HEAD` |

# Removing an upstream
```
git branch --unset-upstream
# or for a specific branch:
git branch --unset-upstream feature/login
```

























