# Lukas's scratchpad of Github tips

## Pipeline

```git status```  
```git add -A``` - track files  
```git diff``` - [see changes](https://stackoverflow.com/questions/2529441/how-to-read-the-output-from-git-diff)  
```git commit -a -m "message"``` - lock tracked files to local computer  
```git push origin master``` - sync local machine changes to online repo  
```git pull origin master``` - clone current copy of origin to local master branch  

* Vim tips when it asks to write a message  
    Press ```i``` to enter insert mode.  
    Type message.  
    Press  <kbd>esc</kbd> to go back to command mode.  
    Then type ```:w``` followed by <kbd>enter</kbd> to save.  
    Finally ```:q``` followed by <kbd>enter</kbd> to quit.


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

## Other core commands
```git diff```  
```git checkout```  
```git branch``` - shows branches including local "master" branch  

## Other useful commands
```git remote show origin``` - which URL is origin  
```git ls-tree -r master``` - list all files in branch named "master"  
```git remote -v``` show URL of "origin"  

## Tutorials I've gone through
* [Software carpentry](https://swcarpentry.github.io/git-novice/)

## Helpful cheatsheets
* [Github visual guide](http://marklodato.github.io/visual-git-guide/index-en.html)