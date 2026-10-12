## get difference
- `git diff`: working tree vs index
- `git diff --staged`: index vs HEAD
- `git diff HEAD`: working tree vs HEAD
- `git diff branch1..branch2`: compare branches

## branch
- `git switch -c <branch name>`: create and switch to branch
- `git checkout <branch name>`: switch to branch
- `git branch -d <branch>`: delete branch (safe)

## working tree operations
- `git reset --hard HEAD`: throws away uncommitted changes
- `git restore --source=HEAD~1 -- path/to/file`: restore file to how it was in previous commit

## merge
- `git merge --squash <branch>`: takes net effect of all commits on `<branch>` and puts changes in working tree/index, but doesn't create commit

## fetch
- `git fetch origin pull/<pr #>/head:<branch>`: create local branch called `<branch>`

## log
- `git log --graph --oneline --decorate --all --color`: view commit records visually
	- `--graph`: draw branch/merge line
	- `--oneline`: one line per commit
	- `--decorate`: shows branch/tag names
	- `--all`: shows all branches
	- `--color`: add color

## commit 
- `git commit --amend --no-edit`: add commit without changing commit message