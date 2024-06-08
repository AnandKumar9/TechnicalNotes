[toc]

##### Working with terminal editor

Pressing any key such as `a` activates the editor.
Pressing `esc` deactivates the editor.
Then `:` followed by commands such as `w` `q` `a` can be typed to indicate what needs to be done with the editor's contents.

`:wq` - Write and commit <br>
`:x` - Save and quit <br>

[link](https://stackoverflow.com/a/13507455/1135417)

> Once you are inside the editor, arrow keys work very fluidly for navigating up and down.

##### Various trick commands 

###### Getting a list of all files that have changed between two commits

```
git log --name-only --pretty=oneline --full-index hash2..hash1 | grep -vE '^[0-9a-f]{40} ' | sort | uniq
```

###### Getting a list of all authors (i.e. every1 who has ever made a commit)

```
git shortlog -s | cut -c8-
```

###### Parsing commit log (`rev-parse`)

`rev-parse` can be used to parse commit logs in several ways. Here are some of the commands. ([Reference](https://git-scm.com/docs/git-rev-parse), [Examples](https://stackoverflow.com/a/41350393/1135417))

```
git rev-parse HEAD <---- Gives commit hash
git rev-parse --abbrev-ref HEAD <---- Gives branch name
```

#### git worktree

> Worktrees can be handy if there is some quick change that needs to be made in a different branch, and you don't want to disturb your current branch or any uncommitted changes in it.

It's an alternate way for creating a copy of any branch or commit of the current working tree, and managing all of these branches together. A similar thing can be achieved by copying the repo, and discarding uncommitted changes, but this can be easier.

The main worktree is called `main worktree` and all the additional worktrees are called `linked worktrees`.

The actual syntax is this. `path` is where the new worktree should be located, and the `newBranchName` is the name of the new branch to be used there.
```
git worktree add <path> <newBranchName>
```

```
git worktree add ../Fix (Creates new workstream named Fix at location ../Fix, from the current commit)
git worktree add ../Fix -b AsiaMore 21d00af (Creates a new workstree named AsiaMore at the path ../Fix, from the specified commit, and creates a branch named AsiaMore)

git worktree remove Fix2  (Removes the mentioned worktree from file system)
git worktree list (Gives a list of current worktrees)
```

When a git branch is created, any branch which is entirely in a different worktree is shown with `+` sign.
```
anand@Anands-MacBook-Air TestGit % git branch
  Africa
* AfricaMore
+ AsiaMore
  Europe
  master

anand@Anands-MacBook-Air TestGit % cd ../Fix
anand@Anands-MacBook-Air Fix % git branch
  Africa
+ AfricaMore
* AsiaMore
  Europe
  master

```

#### Setting up SSH keys

When using SSH, the remotes should have their URL as `git@` like shown below instead of usual absolute URLs.

```
upstream	git@github.cloud.capitalone.com:ease-ios/enterprise.git (fetch)
upstream	git@github.cloud.capitalone.com:ease-ios/enterprise.git (push)
```

This can also be achieved globally by adding the below in `~/.gitconfig` file.
```
[url "git@github.kdc.capitalone.com:"]
  insteadOf = https://github.kdc.capitalone.com/
[url "git@github.kdc.capitalone.com:"]
  pushInsteadOf = "git://github.kdc.capitalone.com/"
[url "git@github.kdc.capitalone.com:"]
  pushInsteadOf = "https://github.kdc.capitalone.com/"
```

General Github documentation for working with SSH keys ([link](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys))

--------

filter branch <br>
git-flow <br>
Submodules & subtrees <br>
Bisect & Blame <br>
Working directory / index / tree <br>

http://git-memo.readthedocs.io/en/latest/filter-branch.html
https://manishearth.github.io/blog/2017/03/05/understanding-git-filter-branch/

