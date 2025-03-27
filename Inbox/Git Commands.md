	

29-10-2024 10:02

Status: #in_progress

Tags:

# Git Commands

- [[Git Commands#Branches|Branches]]
- [[Git Commands#Fetch|Fetch]]
- [[Git Commands#Log|Log]]
- [[Git Commands#rebase|Rebase]]
- 

## Under the hood
*./.git/objects* directory stores all the commits (local and remote)
*./.git/refs/heads/* stores **local** branches
*./.git/refs/remotes/* stored **remote** branches
## Branches
### Inspect
for local branches
``` bash
git branch
```
for remote branches
``` bash
git branch -r
```
### Create
create local
``` bash
git checkout -b new-branch-name
# newer Git versions
git switch -c new-branch-name
# push remote to a new remote branch
git push -u origin new-branch-name
# The `-u` (or `--set-upstream`) flag sets up tracking, so your local branch knows which remote branch to sync with for future pulls and pushes.
```
add repo
``` bash
$ git remote add new-remote-repo https://bitbucket.com/user/repo.git 
```
## Fetch

*git fetch* download the remote content but does not *merge* them as in *git pull*

```
git fetch <remote> <branch>
```
format: *old-hash..new-hash branch-name -> remote-tracking-branch*
example
``` bash
git fetch origin
# current commit a1e8fb5 
a1e8fb5..45e66a4 main -> origin/main # fetching newest commit for branch origin/main 45e66a4
a1e8fb5..9e8ab1c develop -> origin/develop # fetching newest commit for branch origin/develop 9e8ab1c
* [new branch] some-feature -> origin/some-feature # new branch named origin/some-feature
```
### inspect what we have fetched
#### Commits
display from my current commit(excluded) to recently fetched commit
``` bash
# currenly in branch zoom_offload_by_port
git log --oneline HEAD..origin/zoom_offload_by_port
# or more simply
git log HEAD..FETCH_HEAD
# to see the actual differences (the patches/changes) add -p
git log -p HEAD..origin/zoom_offload_by_port
# summary of changes
git diff HEAD origin/zoom_offload_by_port
```

``` bash
git log -p HEAD..origin/zoom_offload_by_port
```
first we *fetch* 
``` bash
# fetch specific branch
git fetch origin zoom_offload_by_port 
```
then we inspect (detached HEAD)
``` bash
git checkout origin/zoom_offload_by_port
```
### Synchronize origin with git fetch
using [[Git Commands#Merge|Mege]] of [[Git Commands#Rebase|Rebase]]
to approve the changes
``` bash
# check out to zoom_offload_by_port if needed
git checkout zoom_offload_by_port 
git merge origin/zoom_offload_by_port
```
#### problems with merge
``` bash
error: Your local changes to the following files would be overwritten by merge:
        source/processes/hpagidecoder/hpagidecoderimpl/CrLearningKpiMngr.cpp
Please commit your changes or stash them before you merge.
```
To inspect the local changes in that file that would be overwritten
``` bash
git diff source/processes/hpagidecoder/hpagidecoderimpl/CrLearningKpiMngr.cpp
# to see conflict in that file
git diff HEAD..FETCH_HEAD source/processes/hpagidecoder/hpagidecoderimpl/CrLearningKpiMngr.cpp
```

you can 
- [[Git Commands#Commit|Commit]]
- [[Git Commands#Stash|Stash]]
- [[Git Commands#Checkout|Discard changes]]
## Log

display log locally
``` bash
git log --oneline --decorate --graph --pretty=format:"%h | %ad | %an: %s" --date=short
```

display log on remote *origin* and branch *master*
``` bash
git log origin/master --oneline
```
display commits that are missing in remote
``` bash
git log origin/master..HEAD
```
## Tracking

The most direct way - shows the current branch and its tracking info
``` bash
git branch -vv
```

For more detailed information about the current branch only
``` bash
git status -sb
# or
git rev-parse --abbrev-ref --symbolic-full-name @{u}
```

To see all tracking relationships for all branches
``` bash
git remote show origin
```


## Rebase

![[Git Commands.png]]
``` shell
git rebase master
```
![[Git Commands-1.png]]

rebase after fetch
``` shell
# checkout to you local branch
git checkout zoom_offload_by_port
# rebase
git rebase origin/zoom_offload_by_port
```
Note: **don't rebase commits that have been pushed to a shared repository**

## Merge
``` bash
# merge
```
## Reset

### moving HEAD pointer (--soft)
``` bash
git reset --soft HEAD~1
git reset --soft B
```
lets say those are my commits: A → B → C
- *git reset --soft B* will move HEAD to point at B, but your working directory will still have all the changes from commit C, and those changes will be staged.
- *git checkout B* will move HEAD to B and update your working directory to match B, discarding the changes from commit C (unless there are uncommitted changes that would be overwritten, in which case Git will prevent the checkout).
*git reset --soft* i mainly used for reorganizing commits:
- **Squashing multiple commits into one**: If you made several small commits that logically belong together, you might want to combine them into a single, more meaningful commit before sharing your code.
- **Reordering commits**: Sometimes you might want to change the order of your commits to make the history more logical.
- **Editing commit messages**: If you made a typo or want to provide a more descriptive commit message.
- **Adding changes to a previous commit**: If you forgot to include some changes in your last commit, rather than making a new "oops, forgot this" commit.


### removing files from staging area(--mixed)
``` bash
# This will remove all files from the staging area but keep your changes in the working directory
git reset --mixed # default
# unstage certain file
git reset --mixed <file-path> # default
```
### unstage files AND discards all changes(--hard)
``` bash
git reset --hard
```
## Stash

## Commit

## Checkout


## References

https://www.atlassian.com/git/tutorials/syncing/git-fetch