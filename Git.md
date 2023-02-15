* Git is used to solve the problem of source control
>![logo](./pictures/git_1.png)
> 4 phases of Git content

Git stages
* Modifed-> files that have changed, but the changes are not yet marked by git
* Staged-> files are marked by git and in the next commit they will be a part of the latest snapshot
* Commited-> file has been committed and the latest snapshot is this one.
* Branches-> when someone wants to make an expiremental change but does not want to affect the main line.

>![logo](./pictures/git_2.png)

* upstream-> from where the code is taken from. i.e if the computer is cloning from github, Github is the upstream.
* Downstream-> where the changes of the code are made on a seperate computer (clones)
>![logo](./pictures/git_3.png)
>As with a stream of water, if you are downstream, you receive whatever floats along the water, and you have to “push” changes upstream.

![logo](./pictures/git_4.png)
* git init-> initlisies your git in that folder
```
cd .git
ls
```
* in this git folder are two important files->head and config 
* Head is the internal representation of the default master class.
## Key Commands
git log-> creates a log of who commited and what they commited.
git status-> gives a status of all the files and their status.
git add-> command tells GIT to start tracking the files in the local index.
git clone _url_-> will clone the git repo from this repo onto your computer.
__git log --oneline__ great way to know what has gone through.
git reset --hard-> will recover to what the git repositary looked like before
## Git branches
* git branch-> prints out all the branches in the repo.
* git branch name_of_branch-> creates new branch
* git checkout branchname->switches to the new branch.
* To rename branches->switch to the branch->use command git branch __-m__ new_name
* To delete a branch -> git branch -d name_of_branch
## Git Merge
* Used to merge branches-> the chnages are made to the branch which you are currently on.
* EG-> there are two branches-> master and feature_branch you are currently on master-> master has file.txt and feature has file2.txt -> __git merge feature_branch__ merges the two branches
* Use __git log__ to check the new merge commit and __ls__ to see the new files.
> Merge conflicts-> When Git cannot decide on what to change and what to keep
> To fix this we just change the files so that they are consistant-> if there is one line written on one file and the other does not, it git automatically merges them
> However if there are lines were one file says something and another says something else you need to merge 

## Remote repositories
* eg github is a remote repository, where you need to push the changes onto this repo
* the git remote add <name> <url_to_remote_repo>-> most commonly named git remote add <origin> <url_to_remote_repo> 
* after this you can git push
* if you are working on the master branch and are trying to push to remote named origin you need to use __git push origin master__ or in other words __git push <remote_repository> <branch_name>__ 
* git clone <url> will clone the github onto your local machine.
* git fetch <name_of_remote> is used when there are numerous other people working on a project-> where git fetch will make it so that it does not change what is on your local repo. After that you can merge by git merge <origin(name_of_remote)/master(branch_local)>
* git pull <remote_name(origin)> branch_name-> this merges the changes on your machine with the branch. (this downloads and merges automatiicaly, while fetch doesn't)
* git revert will go back to a stage where the code worked.
* Pull requests are barriers before any branch can be merged onto the main-> hence needs to be approved.

## Git Rebase
* If you haven't changed your local repo in a while and there are changes in the remote repo, you need to __git rebase <branch>__ so that your local reposiory is updated. Note this may cause some merging conflicts.
* git rebase vs git merge -> merging results in a new merge commit-> while in rebase it looks like it was taken from a recent parent branch.
* reverting a rebase is much harder than reverting a merge
* recommonended to use rebase for a large amount of people and merge for a small amount





