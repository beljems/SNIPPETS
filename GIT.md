# GIT

```sh
Branch - movable pointers to a commit

	master -> master(09384f)
				|
			develop(09384f) -> develop(0385ff)
				|
			feature(09384f) ->  feature(0355ff)```


## Git CheatSheet
Linus Torvalds - developer of git
man git - manual of git

```sh
git branch - list of all local branches
git branch —remote - list of all remote branches

git checkout — <file> - abandon changes on <file>

git checkout <branch> - switch to branch
git checkout -b <branch> - create branch

git fetch - downloads object/refs from remote branch
	fetching only retrieves the changes, it does not update your local
	-train yourself on remote/local branches
	-more control on merging strategies
	-you can leave merging for later

ex. Up and down icon in sourcetree

git pull - download and then merge
		Git fetch && git merge

git fetch - updates the ref/head but not the working copy
is the command that tells your local git to retrieve the latest meta-data info from the original
(yet doesn’t do any file transferring. It’s more like just checking to see if there are any changes available)

git pull - executes git fetch then git merge
on the other hand does that AND brings (copy) those changes from the remote repository

git commit --amend - return to previous commit
git revert --soft [commit id]
git revert --hard [commit id]

git reset --soft HEAD~1 - not yet push to any branch
-last commit

git reset --hard HEAD^
 - last commit

git reset --hard HEAD~2
- 2 last commits
-
git reset HEAD {file} - onstage file

git branch -m {new_name} - renaming current branch```

### Git Flow
```sh
Init Repository
	- production branch - master
	- development branch - develop
	- feature prefix - feature/
	- hotfix prefix - hotfix/
	- release prefix - release/

New feature
	- branch: develop
	- git checkout develop && git checkout -b feature/feature-name

Finish feature
	- merge to develop
	- push develop(option: delete feature-branch in remote)
	- git push origin feature/feature-name
	- git checkout develop && git merge feature/feature-name
	- git push origin develop
	- git push origin :feature/feature-name

Hotfix
	- when your project is already in prod and you need to fix something

New hotfix
	- branch: master
	- git checkout master && git checkout -b hotfix/hotfix-name
Finish Hotfix
    - git push origin hotfix/hotfix-name
    - git checkout develop && git merge hotfix/hotfix-name -- update develop with hotfix
    - git push origin develop
    - do release

Release
New Release
    - branch: develop
    - when you finish your project phase
    - git checkout develop && git checkout -b release/v1.0.0

Finish Release
    - git checkout master && git merge release/v1.0.0
    - git tag v1.0.0 --create tag or git tag v1.0.0
    - git push origin master v1.0.0 release/v1.0.0 or git push origin master v1.0.0

Cherry Pick
Git cherry-pick commit code

Rebase
Drop - drop specific commit
squash - combine specific commit```
