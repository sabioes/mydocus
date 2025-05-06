# Git

For full documentation visit [git-scm.org](https://git-scm.com/doc).

## Commands

In root folder project:

Delete branches that are only in local repo and workspace. Intended to be used after the pull request successed:
```bash
git fetch --prune && git branch -vv | awk '/: gone]/{print $1}' | xargs -r git branch -d
```

Get last changes on main into feature branch: 
```bash
# Make sure you're on your feature branch
git checkout my-feature-branch
#Fetch all in origin to latest state
git fetch origin
#Merge main into current feature branch
git merge origin/main
```