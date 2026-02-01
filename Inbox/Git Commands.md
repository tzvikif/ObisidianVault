	

29-10-2024 10:02

Status: #in_progress

Tags:

# Git Commands

- [[git commands#branches|branches]]
	- [[git commands#branch Inspect|inspect]]
	- [[git commands#rename|rename]]
	- [[git commands#create branch|create]]
	- [[git commands#delete|delete]]
- [[git commands#fetch|fetch]]
- [[git commands#log|log]]
- [[git commands#rebase|rebase]]
- [[git commands#stash|stash]]
- [[git commands#reset|reset]]
- [[git commands#config|config]]
- [[git commands#clean|cleaning]]
- [[Git Commands#worktree|worktree]]
- [[Git Commands#Cherry-pick|cherry-pick]]
- [[Git Commands#worktree|worktree]]
- [[Git Commands#diff|diff]]
- [[Git Commands#revert|revert]]
- [[Git Commands#inspect|inspect]]
	- [[Git Commands#in Index|index]]
	- [[Git Commands#in commit|commit]]
	- 


## Under the hood
*./.git/objects* directory stores all the commits (local and remote)
*./.git/refs/heads/* stores **local** branches
*./.git/refs/remotes/* stored **remote** branches
## Branches
### branch Inspect
for local branches
``` bash
git branch
```
for remote branches
``` bash
git branch -r
git branch -a # local and remote
```
### change branch
``` bash
git checkout <branch name>
git checkout -f <branch name> # 
```
### rename
 
if you are on the branch you want to change
``` bash
git branch -m  <new branch name>
```
if your are on branch different branch
``` bash
git branch -m <current branch name> <new branch name>
```

### Create branch
create local
``` bash
# create and switch
git checkout -b my_branch [<another branch>]
# newer Git versions >= 2.23
git switch -c my_branch [<another branch]
# create local branch from remote branch
git checkout -b my-local-branch origin/feature/xyz
# create without switching
git branch my_branch [<another branch>]
```
flags:
-c / -b : create branch and switch to it
-C / -f : force create/overwrite if it already exists

create remote
``` bash 
git push -u origin my_branch 
# creates origin/my_branch on the remote. and sets upstream tracking
# my_branch -> origin/my_branch
# The `-u` (or `--set-upstream`) flag sets up tracking, so your local branch knows which remote branch to sync with for future pulls and pushes.
# if you forgot the -u
git branch --set-upstream-to=origin/my_branch
# or
git branch -u origin/my_branch my_branch
```

add repo
``` bash
$ git remote add new-remote-repo https://bitbucket.com/user/repo.git 
```
### delete
``` bash
git push -d <remote_name> <branchname>   # Delete remote
git branch -d <branchname>               # Delete local
```

## Fetch

*git fetch* download the remote content but does not *merge* them as in *git pull*

```
git fetch <remote> <branch>
git fetch --all --prune # fetch everything and removes deleted remotes
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
**remark**: the commands above **do not contact the remote server at all**.
they are checking origin/zoom_offload_by_port locally.
if you want to be sure your *origin/branch*  is up to date, you need first to fetch it.

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
# what did HEAD add?
git log origin/master..HEAD
```
display commits that are added by A or by B but not both.
``` shell
# Commits unique on either side. rarely used.
git log A...B
```
## Tracking
### inspect tracking

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
``` shell
git rebase --onto <newbase> <upstream> <branch>
```
[[git_rebase_onto.excalidraw]]

force your commit in case you changed history. and you want you commit on the server
``` shell
git push --force-with-lease origin master
```


## Merge
``` bash
# merge
```
## Reset

### moving HEAD and current branch pointer (--soft)
``` bash
git reset --soft HEAD~1
git reset --soft B
```
lets say those are my commits: A → B → C
- *git reset --soft B* 
	- move *HEAD* and *branch name* to point at B
	- working directory and index are unchanged. 
- *git checkout B* [--mixed]
	- will move *HEAD* and *branch name* to point at B. 
	- updates index to match B.
	- working directory is unchanged. 
- *git checkout B* --hard
	- will move *HEAD* and *branch name* to point at B. 
	- updates index to match B.
	- working directory matches index. 


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
if you can't merge/rebase because uncommitted changes:
``` bash
git stash
git rebase origin/zoom_offload_by_port
git stash pop

```
## Commit
Modify the contents of the last commit
``` shell
# edit
git add <what you want>
git commit --amend
# or
# edit
git add <what you want>
git reset --soft HEAD~1
git commit
```
**Notice**: git --amend changes commit hash.
## Config
### set
``` bash
git config --global user.name "tzviki"
git config --global user.email "tzviki.fisher@radcom.com"
# rebase on pull for repo
git config pull.rebase true
# or for specific branch
git config branch.<branchname>.rebase true
```
### check current setting
``` shell
git config --get pull.rebase
```

## Clean
remove all untracked files
``` shell
# observe what is being deleted (--dry-run, -n)
git clean -n -d 
git clean -f -d
git clean -fdn # review first 
# delete specific path only
git clean -f -d path/to/dir
```
-d: recursive
-f: force (git won't delete otherwise)
-n (--dry-run): dry run. nothing is being done. just displaying.

### discard changes
``` shell
git checkout .
git restore . # same as above but newer syntax
git restore --staged . # remove from index
```
- Discards working directory changes
- Leaves index and HEAD untouched

## push
- first push. or 
- you want to connect current branch to another remote branch
``` shell
git push -u origin HEAD:master
```
HEAD:master = source:destination
*Push my current branch **to** the remote branch named `master`.*
-u: sets tracking. After this, consider `origin/master` the upstream of my **current local branch**
more common use
``` shell
git push -u origin my-branch
```

## inspect
### in Index
display files in the index(tracked) and optionally working tree
``` shell
git ls-files [folder]
# display untracked files
git ls-files --others --exclude-standard
git ls-files --stage # mode 0: normal, 1/2/3 conflict stages
# <mode> <blob> <stage> <path>
# display ignored files
git status --ignored
```
options
--stage:  staged info
-m : display modified files
### in commit
``` shell
# list file in a commit
git ls-tree -r <commit> [folder]
# display files in last commit
git show --name-only --pretty="" HEAD
git show <commit>:[<file_path>]
# shows diff for a file
git show <commit> -- <file_path>
# shows commits that changes that file
git log <commit> -- <file_path> 
# same as above. with patches.
git log -p <commit> -- <file_path>
# Inspect the file without remembering paths (search)
git grep "some text" <commit> -- [<path>]
# files that changes at least once in the last 10 commits.
git log -n 10 --name-only --pretty=format: | sort -u
# same as above with status
git log -n 10 --name-status --pretty=format: | sort -u
# display files changes only in mainline
git log --first-parent --name-only
```
-r : list all files recursively

### working tree
Temporarily check out a file from a commit
replaces the file on disk
``` shell
git checkout <commit> -- path/to/file
# or newer version
git restore --source=<commit> path/to/file
```

## Cherry-pick
This creates a **new commit** on your current branch with the same changes but a different hash
``` shell
git cherry-pick <commit-hash>
git cherry-pick <start-hash>..<end-hash>
# bring the changes without commit
git cherry-pick --no-commit <commit> [<commit2> <commit3>] 
```

## worktree

A *worktree* allows you to have multiple branches of the same repository checked out simultaneously in different folders

add worktree
``` shell
# creating new branch
git worktree add <path> -b <new-branch-name>
# example
git worktree add ../wt-feature feature
# existing branch
git worktree add <path> <existing-branch-name>
```
- It is best practice to create the new worktree folder **outside** of your current project directory (using `../`) to avoid confusing Git with a repository inside another repository.
- submodules.  git submodule update --init --recursive to begit cont.


``` shell
# list worktree locations
git worktree list
# remove worktree
git worktree remove <path-to-worktree-folder>
# 
```

in case uncommitted changes git will block removal.
``` shell
git worktree remove -f <path-to-worktree-folder>
```
delete the branch itself
``` shell
git branch -D worktree-2025-12-28T08-57-58
```
if removed manually the folder. clean it using
``` shell
git worktree prune
```

## Inspect changes
### show
**Commit metadata** (author, date, message)
**The patch** introduced by that commit
for reviewing a commit
``` shell
git show <commit> # default target HEAD
# show only the patch
git show --stat
git show --name-only
```
### diff
Shows differences between two states.
Those snapshots can come from:
- the **working tree**
- the **index**
- a **commit**
- the **merge base** of two commits
![[Git Commands diff.png]]
``` shell
git diff # shows working tree vs index (should show your edits if any)
git diff HEAD [--working-tree] # Working tree vs HEAD
git diff --staged # shows index vs HEAD
# Show me the changes needed to go from <commit1> to <commit2>
git diff <commit1> <commit2> [--name-only]
# everything that is different between <branch1> and <branch2>
# no ancestry logic involved. confusing for PR 
git diff <branch1>..<branch2>
# tree(merge-base(A,B)) ↔ tree(B). what <branch2> added since diverged from A. 
git diff A...B

```

## revert
create a commit that *undo* the commit
``` shell
git revert 
```

## References

https://www.atlassian.com/git/tutorials/syncing/git-fetch