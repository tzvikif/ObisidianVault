

29-10-2024 10:02

Status: #in_progress

Tags:

# Git Commands

- [[Git Commands#Branches|Branches]]
- [[Git Commands#Fetch|Fetch]]
- 


## Branches

for local branches
``` git
git branch
```
for remote branches
``` git
git branch -r
```

## Fetch

*git fetch* download the remote content but does not *merge* them as in *git pull*

### Under the hood
*./.git/objects* directory stores all the commits (local and remote)
*./.git/refs/heads/* stores **local** branches
*./.git/refs/remotes/* stored **remote** branches

```
git fetch <remote> <branch>
```
example
```
git fetch origin

a1e8fb5..45e66a4 main -> origin/main
a1e8fb5..9e8ab1c develop -> origin/develop 
* [new branch] some-feature -> origin/some-feature
```

### inspect what we have fetched
first we *fetch*
```
git fetch coworkers_repo coworkers/feature_branch fetching coworkers/feature_branch
```
then we inspect (detached HEAD)
```
git checkout coworkers/feature_branch
```
### Synchronize origin with git fetch

![[Git Commands fetch.png]]

to view commit that were added to the *upstream main*
```
git log --oneline main..origin/main
```

to approve the changes
```
git checkout main 
git log origin/main
git merge origin/main
```


## References

https://www.atlassian.com/git/tutorials/syncing/git-fetch