# 05- Cloning a Repository

To clone a repository we need the repository url. For example: **_`https://github.com/jmschp/mosh-ultimate-git-course.git`_**.

Then in our machine we run the command `git clone <url>`, this will create a local copy of the repository. This command only copies the **_`main`_** branch, which is the default branch, even if there are other branches in the **Remote Repository**.

```zsh
❯ git clone https://github.com/jmschp/mosh-ultimate-git-course.git
Cloning into 'mosh-ultimate-git-course'...
remote: Enumerating objects: 489, done.
remote: Counting objects: 100% (489/489), done.
remote: Compressing objects: 100% (308/308), done.
remote: Total 489 (delta 236), reused 422 (delta 169), pack-reused 0
Receiving objects: 100% (489/489), 5.90 MiB | 1.71 MiB/s, done.
Resolving deltas: 100% (236/236), done.
```

## Changing the default directory

When using the `clone` command Git will create a directory with the same name of the repository. In ths case `mosh-ultimate-git-course`. We can change it by passing a new name after the url `git clone <url> <my-folder>`

```zsh
git clone https://github.com/jmschp/mosh-ultimate-git-course.git mosh-git
```

The above command will copy the repository to a new folder called `mosh-git`.

## Remote Repository

When we clone a **Remote Repository**, in this case from GitHub, Git names this source repository **_`origin`_**.

```zsh
❯ git log --oneline --graph
* 0065a18 (HEAD -> main, origin/main, origin/HEAD) start new lesson
* 488cbba lesson complete
* 910d1d3 renamed folder
* a32bc1f style: removed white spaces
* 2d4c7af fixed merge conflict
* 5a090b1 rename file
```

### Reference `origin/main`

## The Three "States" of Your Branch
# When you are working, there are actually three different versions of "main" to keep track of:

1. main (Local): This is your active workspace. When you type git commit, this pointer moves forward.
2. origin/main (Remote Tracking): This is a local pointer that marks where the main branch was on the server (GitHub) the last time you ran git clone, git fetch, or git pull.
3. main (On GitHub): The actual branch living on the server.

### List remote repositories

We can have more than one **Remote Repositories**, with the command `git remote` we can list all the **Remote Repositories** connected to our **Local Repository**.

```zsh
❯ git remote -v
origin  https://github.com/jmschp/mosh-ultimate-git-course.git (fetch)
origin  https://github.com/jmschp/mosh-ultimate-git-course.git (push)
```

Using the `-v` option we get a more verbose output, showing more details. In this example we only hev one **Remote Repository**.
