# Lukas's scratchpad of Github tips

**I did many small commits here to learn about ```git```, so forking this repo will clutter your commit history.**  
**I recommend you download zipfile and copy into new repo. Or use ```git clone --depth 1 https://github.com/lahoffm/github_help.git```.

## Simple pipeline (*best practice: don't commit to master, commit to branches then merge with master*)
```git status```  
```git add -A``` - track files in staging area for commits
```git diff``` - [see changes](https://stackoverflow.com/questions/2529441/how-to-read-the-output-from-git-diff)  
```git commit -am "message"``` - lock tracked files to local computer  
```git push origin master``` - sync local master branch to online repo  
```git pull origin master``` - clone current copy of origin to local master branch  

## Working with branches
```git checkout -b mybranch``` - switch to branch (```-b``` is to create & checkout in 1 step)  
```git branch``` - list branches in repo and current branch  
```git add -A``` - if files were staged in master they are also staged in branch but good to do in case new files are made  
```git commit``` as usual within the branch  
```git push origin mybranch``` - sync local mybranch branch to online repo  
```git merge mybranch --no-ff --m "merging mybranch into master``` - mybranch = name of branch you want to merge with current branch (such as master).  
	Make sure you're in the branch you want to merge to! ```--no-ff``` - no fast-forward (can add or reduce confusion on case-by-case basis)  
* Solve merge conflict
	* open file with conflict
	* Delete conflict marker lines containing ```<<<<<<<```, ```=======```, ```>>>>>>>```
	* Make the changes you want to see in the final merge
	* ```git add .```
	* ```git commit -m "resolved merge conflict"```
```git branch -d mybranch``` - delete local branch  
```git push origin --delete mybranch``` - delete remote branch  
```gitk --all``` - visualize commit tree

## [Undoing](https://github.com/blog/2019-how-to-undo-almost-anything-with-git) [commits](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting)

* Restoring single file locally
```HEAD``` - most recent commit, ```HEAD~1``` = one commit before ```HEAD```  
```git log --oneline -5``` - see unique identifiers for last 5 commits  
```git log --patch src/helloworld.py``` - narrow down which commit you want to restore  
```git checkout c6fab02 src/helloworld.py```  
```git commit –a –m “restore helloworld.py from commit c6fab02”```  
* Restore everything locally to where it was after a prior commit (*use with caution*)
```git reset --hard c6fab02```  
* Restore after pushing to remote repo
```git revert``` - but safest way is to just fix the bad code locally and push a new commit  

## Other useful commands 
```git remote -v``` - remote URLs (such as origin)  
```git ls-tree -r master``` - list all files in branch named "master"  

## Nice tutorials & guides
* [Pro Git ebook](https://git-scm.com/book/en/v2)
* [Software carpentry](https://swcarpentry.github.io/git-novice/)
* [Atlassian git tutorials](https://www.atlassian.com/git/tutorials/)
* [Git concepts simplified](http://gitolite.com/gcs.html#(1))
* [Github visual guide](http://marklodato.github.io/visual-git-guide/index-en.html)
* [Gitk tutorial](https://lostechies.com/joshuaflanagan/2010/09/03/use-gitk-to-understand-git/)
* [Aha moments when learning git](https://betterexplained.com/articles/aha-moments-when-learning-git/)
* [A successful git branching model](http://nvie.com/posts/a-successful-git-branching-model/)
* [Git best practices](https://gist.github.com/pandeiro/1552496)
blabla
## Nice cheatsheets
* [PDF from rogerdudler.github.io/git-guide](git_cheat_sheet.pdf)
* [PDF from education.github.com](git-cheat-sheet-education.pdf)

## Instructions to contribute to group project repos - still in draft form

* [Git Pro Section 6.2 - Contributing to a Project](https://git-scm.com/book/en/v2/GitHub-Contributing-to-a-Project)
* Use git fetch/merge instead of just git pull?
* git tag?
* git clone the repo into own computer, then fork the repo (in browser)
* cd to the folder ht-archive
* git branch, should say master
* git remote rename origin upstream 
* git remote add origin <your_url> such as https://github.com/lahoffm/ht-archive.git (the URL you see in browser when you click on the “Clone or Download”)
* git branch my_branch_name [no spaces] - whenever you start working on something
* git checkout my_branch_name
* git status - should say you are on branch my_branch_name instead of master
* Now start working on the code
* git commit
* git push origin my_branch_name - pushes the branch to your fork of ht-archive online
* git checkout master - go back to master
* git pull -r upstream master - pull from the upstream code (anidata/ht-archive) into master
* Now if you do git checkout my_branch_name, then git pull -r upstream master then the branch will be updated into the latest version of the upstream repo (anidata/ht-archive)?? Not sure if this is how it works.
* Philosophy: you want your local “master” to always be up-to-date with the upstream repo (i.e. anidata/ht-archive) and then you work on your local branch (which you push to your fork online)

