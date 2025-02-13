	

29-10-2024 10:02

Status: #in_progress

Tags:

# Git Commands

- [[Git Commands#Branches|Branches]]
- [[Git Commands#Fetch|Fetch]]
- [[Git Commands#Log|Log]]
- 

## Under the hood
*./.git/objects* directory stores all the commits (local and remote)
*./.git/refs/heads/* stores **local** branches
*./.git/refs/remotes/* stored **remote** branches
## Branches

for local branches
``` bash
git branch
```
for remote branches
``` bash
git branch -r
```
creating remote branches
``` bash
$ git remote add new-remote-repo https://bitbucket.com/user/repo.git # Add remote repo to local repo config 
$ git push <new-remote-repo> crazy-experiment~ # pushes the crazy-experiment branch to new-remote-repo
```
## Fetch

*git fetch* download the remote content but does not *merge* them as in *git pull*

```
git fetch <remote> <branch>
```
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


## Stash

## Commit

## Checkout

``` bash
git checkout -- source/processes/hpagidecoder/hpagidecoderimpl/CrLearningKpiMngr.cpp
```


## References

https://www.atlassian.com/git/tutorials/syncing/git-fetch