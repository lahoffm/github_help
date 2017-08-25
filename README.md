# Lukas's scratchpad of Github tips

**I did many small commits to learn about Github, so if you fork this repo that will clutter up your commit history.**  
**I recommend you download zipfile and copy into new repo. Or use ```git clone --depth 1 https://github.com/lahoffm/github_help.git```.

## Pipeline
```git status```  
```git add -A``` - track files in staging area for commits
```git diff``` - [see changes](https://stackoverflow.com/questions/2529441/how-to-read-the-output-from-git-diff)  
```git commit -am "message"``` - lock tracked files to local computer  
```git push origin master``` - sync local master branch to online repo  
```git pull origin master``` - clone current copy of origin to local master branch  

* Vim tips when it asks to write a message  
    Press ```i``` to enter insert mode.  
    Type message.  
    Press  <kbd>esc</kbd> to go back to command mode.  
    Then type ```:w``` followed by <kbd>enter</kbd> to save.  
    Finally ```:q``` followed by <kbd>enter</kbd> to quit.

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

### Restoring single file locally
```HEAD``` - most recent commit, ```HEAD~1``` = one commit before ```HEAD```  
```git log --oneline -5``` - see unique identifiers for last 5 commits  
```git log --patch src/helloworld.py``` - narrow down which commit you want to restore  
```git checkout c6fab02 src/helloworld.py```  
```git commit –a –m “restore helloworld.py from commit c6fab02”```  

### Restore everything locally to where it was after a prior commit (*use with caution*)
```git reset --hard c6fab02```  

### Restore after pushing to remote repo
```git revert``` - but safest way is to just fix the bad code locally and push a new commit  

## Other useful commands
```git diff```  
```git remote -v``` - remote URLs (such as origin)  
```git ls-tree -r master``` - list all files in branch named "master"  


## Tutorials I've gone through
* [Software carpentry](https://swcarpentry.github.io/git-novice/)
* [Atlassian git tutorials](https://www.atlassian.com/git/tutorials/)
* [Gitk tutorial](https://lostechies.com/joshuaflanagan/2010/09/03/use-gitk-to-understand-git/)

## Tutorials I'd like to go through
* [Git-scm ebook](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository#Ignoring-Files)

## Helpful cheatsheets
* [Github visual guide](http://marklodato.github.io/visual-git-guide/index-en.html)
* [Git concepts simplified](http://gitolite.com/gcs.html#(1))