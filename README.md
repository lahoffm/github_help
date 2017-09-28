# Atlanta BEST scratchpad of Github tips

## Installing git
1. Get a [Github](https://git-scm.com/download/) account
2. Download latest version of Git
	* For Windows, I like using **git bash**. Download it [here](https://git-for-windows.github.io/).
	* For Mac, download git [here](https://git-scm.com/download/) and you can run it from the Terminal.
	* For Linux, install git [here](https://git-scm.com/download/linux).
3. Do the setup steps described [here](https://swcarpentry.github.io/git-novice/02-setup/)
4. Set up credentials, to avoid [annoyance of entering password](https://help.github.com/articles/why-is-git-always-asking-for-my-password/) each time you connect to Github
	* *Not sure how to do this step-by-step on Windows and Mac*.

## Nice tutorials & guides
* [Pro Git ebook](https://git-scm.com/book/en/v2)
* [Git tutorial - Try Git](https://try.github.io/levels/1/challenges/1)
* [Github for beginners](https://readwrite.com/2013/09/30/understanding-github-a-journey-for-beginners-part-1/)
* [An intro to Git and Github for beginners](http://product.hubspot.com/blog/git-and-github-tutorial-for-beginners)
* [Git - the simple guide](http://rogerdudler.github.io/git-guide/)
* [Software carpentry](https://swcarpentry.github.io/git-novice/)
* [Atlassian git tutorials](https://www.atlassian.com/git/tutorials/)
* [Git concepts simplified](http://gitolite.com/gcs.html#(1))
* [Github visual guide](http://marklodato.github.io/visual-git-guide/index-en.html)
* [Gitk tutorial](https://lostechies.com/joshuaflanagan/2010/09/03/use-gitk-to-understand-git/)
* [Aha moments when learning git](https://betterexplained.com/articles/aha-moments-when-learning-git/)
* [A successful git branching model](http://nvie.com/posts/a-successful-git-branching-model/)
* [Git best practices](https://gist.github.com/pandeiro/1552496)

## Nice cheatsheets
* [PDF from rogerdudler.github.io/git-guide](git_cheat_sheet.pdf)
* [PDF from education.github.com](git-cheat-sheet-education.pdf)
* [PDF Markdown cheatsheet from Github Guides](markdown-cheatsheet.pdf)
* [Basic Git commands](https://confluence.atlassian.com/bitbucketserver0414/basic-git-commands-895367449.html)

## Simple pipeline (*best practice: don't commit to master, commit to branches then merge into master*)
```git status```  
```git add -A``` - track files in staging area for commits  
```git diff``` - [see changes](https://stackoverflow.com/questions/2529441/how-to-read-the-output-from-git-diff)  
```git commit -am "message"``` - commit tracked files to local computer.  
```git commit -a -m "Main commit message" -m "Second paragraph with more details"``` - commit multiple paragraphs.  
```git push origin master``` - sync local ```master``` branch to online repo's ```master``` branch [Explanation](https://git-scm.com/docs/git-push#git-push-codegitpushoriginmastercode)  

## Working with branches
```git checkout -b mybranch``` - switch to branch (```-b``` is to create & checkout in 1 step)  
```git branch``` - list branches in repo and current branch (```-a``` option will also show [remote-tracking branches](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches))  
```git add -A``` - if files were staged in master they are also staged in branch but good to do in case new files are made  
```git commit``` as usual within the branch  
```git push origin mybranch``` - sync local branch ```mybranch``` to online repo's branch ```mybranch```  
```git merge mybranch --no-ff --m "merging mybranch into current branch"``` - mybranch = name of branch you want to merge with current branch (such as master).
**Make sure you're in the branch you want to merge to!** ```--no-ff``` - no fast-forward (can add or reduce confusion on case-by-case basis)  
* Solve merge conflict
	* Open file with conflict
	* Delete conflict marker lines containing ```<<<<<<<```, ```=======```, ```>>>>>>>```
	* Make the changes you want to see in the final merge
	* Save file
	* ```git add .```
	* ```git commit -m "resolved merge conflict"``` 
* Solve merge conflict during pull requests
	* [Solve from local repository](https://github.com/AgileVentures/MetPlus_PETS/wiki/Resolving-Pull-Request-merge-conflicts).
	* [Solve from Github](https://help.github.com/articles/resolving-a-merge-conflict-on-github/).

```git branch -d mybranch``` - delete local branch  
```git branch -rd upstream/master``` - delete remote-tracking branch locally. Doesn't delete the remote branch on Github.  
```git push origin --delete mybranch``` - delete remote branch  
```git push origin master``` - don't forget to push "the branch that you merged into" to the remote too!  
```gitk --all``` - [visualize commit tree](https://lostechies.com/joshuaflanagan/2010/09/03/use-gitk-to-understand-git/)  

![gitk](img/gitk-example.png)


## [Undoing](https://github.com/blog/2019-how-to-undo-almost-anything-with-git) [commits](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting) (Only use locally)

* Restoring single file locally
```HEAD``` - most recent commit, ```HEAD~1``` = one commit before ```HEAD```  (read the docs on how HEAD pointers work)
```git log --oneline -5``` - see unique identifiers for last 5 commits  
```git log --patch src/helloworld.py``` - narrow down which commit you want to restore (gives list of SHAs - Secure Hash Algorithm values uniquely identifying the commit)  
```git checkout c6fab02 src/helloworld.py``` - checkout a file from the commit whose SHA started with ```c6fab02```  
```git commit –a –m “restore helloworld.py from commit c6fab02”```  - commit the file you checked out, which was from an earlier commit
* Restore everything locally to where it was after a prior commit (*use with caution*)
```git reset --hard c6fab02```  
* Make a new branch starting at a previous commit  
```git checkout c6fab02; git checkout –b mybranch```
* Undoing a merge
	* Haven't tried this but here's [two](http://www.deferredprocrastination.co.uk/blog/2012/git-un-merge/) [sites](https://mijingo.com/blog/reverting-a-git-merge)
* Restore after pushing to remote repo  
```git revert``` - but safest way is to just fix the bad code locally and push a new commit  

## Other useful commands 
```git remote -v``` - remote URLs (such as origin)  
```git ls-remote``` - references in remote repo  
```git ls-tree -r master``` - list all tracked files in branch named "master"  
```git tag```, ```git push origin --tags```, etc. - [tag stable versions of your code](https://git-scm.com/book/en/v2/Git-Basics-Tagging) and push them online so people can download ["Release v1.5"](https://help.github.com/articles/working-with-tags/) for example  

## How to contribute to group project repos
### Explanations
* [Pro Git Ebook Section 6.2: Github - Contributing to a Project](https://git-scm.com/book/en/v2/GitHub-Contributing-to-a-Project)
* [scikit-learn-sprint-instructions (PDF)](https://github.com/amueller/talks_odt/raw/master/2017/scikit-learn-sprint-instructions.pdf)
* [Contributing - scikit-learn](http://scikit-learn.org/stable/developers/contributing.html)
* [Contributing to Numpy](https://docs.scipy.org/doc/numpy/dev/)
* [Git fetch and merge](https://longair.net/blog/2009/04/16/git-fetch-and-merge/)
* [Difference between git pull and git fetch](https://stackoverflow.com/questions/292357/what-is-the-difference-between-git-pull-and-git-fetch)

### General fork-merge workflow ([Source](https://git-scm.com/book/en/v2/GitHub-Contributing-to-a-Project))
1. Fork the project.  
2. Create a topic branch from master.  
3. Make some commits to improve the project.  
4. Push this branch to your GitHub project.  
5. Open a Pull Request on GitHub.  
6. Discuss, and optionally continue committing.  
7. The project owner merges or closes the Pull Request.  

### Example fork-merge pipeline
* Fork the group project repo (in browser)
* ```cd``` to a folder in command line
* ```git clone "https://github.com/my-username/my-reponame.git"``` - copy forked repo to your computer
* ```cd my-reponame``` - do all subsequent git commands from the repo's local folder
* ```git remote add upstream https://github.com/group-username/group-reponame.git``` - track a remote repo called ```upstream```. This should be the group project repository that you just forked.
* ```git remote -v``` - shows ```origin``` is the repo that you forked, the URL should have **your** username. Everything you push to ```origin``` will go to a repo under **your** username. There should also be a remote called ```upstream```.
* ```git checkout -b mybranch``` - make a new branch
* Write code, make some commits to ```mybranch```.
* Make sure your local ```master``` and ```mybranch``` are always up-to-date with the ```upstream/master``` branch!
	* Get changes from ```upstream/master``` branch into local ```master``` branch
		* ```git checkout master``` - *subsequent bullets assume you're in ```master``` branch.*
		* **Method 1:** ```git pull -r upstream master``` - Pull upstream ```master``` branch into **currently checked out** local branch *(should be ```master``` branch)*. ```-r``` option is to [rebase](https://www.atlassian.com/git/tutorials/merging-vs-rebasing) (otherwise it would do a merge).
		* **Method 2:** *safer than Method 1 because you can examine changes before merging*
			* ```git fetch upstream master``` - fetch ```master``` branch of ```upstream``` repo but don't merge or rebase yet, in other words "update my local copy of ```upstream/master``` branch"
			* ```gitk --all```, ```git diff master..upstream/master```, ```git log --oneline master..upstream/master``` - See differences between local ```master``` and fetched ```upstream/master```
			* ```git merge upstream/master``` - merge fetched ```upstream/master``` branch into **currently checked out** local branch (*should be ```master``` branch)*.
		* Now, local ```master``` branch is up-to-date with upstream repo's ```master``` branch.
	* Merge those changes to ```mybranch```, so it stays up-to-date with ```upstream/master``` branch.
		* ```git checkout mybranch``` - *subsequent bullets assume you're in ```mybranch```*
		* ```git diff master..mybranch``` - difference from ```master``` to ```mybranch```. For example, if a commit on mybranch added "123", it shows up as +123, meaning "123 added, relative to master".
		* ```git merge master``` - merge ```master``` into ```mybranch```.
		* Resolve any merge conflicts. *Try to avoid edits conflicting with new features in ```upstream/master``` so your feature can be pulled seamlessly into main codebase later.*
	* Now, your local ```master``` and the group project repo's ```master``` (```upstream/master```) are identical, and ```mybranch``` has successfully incorporated the latest state of the codebase, plus your new feature.
* ```git push origin master; git push origin mybranch``` - push ```master``` and ```mybranch``` to **your own repo**.
* In browser, initiate [pull request](https://git-scm.com/book/en/v2/GitHub-Contributing-to-a-Project) from ```mybranch``` when it's ready to be merged into the group project's master branch (```upstream/master```).
* Monitor comments in pull request, make more commits/comments as needed until they merge and close pull request.
	* If someone submits a pull request to your repo, [checkout the pull request](https://help.github.com/articles/checking-out-pull-requests-locally/) and test locally before merging it on Github.
* Pull the updated ```upstream/master``` back into your local ```master``` branch and delete ```mybranch```, since your work is now merged to the main codebase.
