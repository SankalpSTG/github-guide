# Git Practice Repo

Learn with me...

## If You Have Git Configured
or you have github desktop installed and you have pushed / pulled something to github atleast once.

Create an empty folder and open terminal in that folder and type

```
git init
```
The above line will initialize your git repository.

Then create a file README.md and write something inside that file. You can also do this via terminal itself.
```
echo "# Git Practice Repo"
```
then in the terminal, write
```
git add READMD.md
```
then write
```
git commit -m "My first commit"
```
After this, you will have to go to github.com, create an empty repo and copy the https link with you.

In terminal, write
```
git remote add origin <your-repo-url>
```
Now rename your branch to "main"
```
git branch -M main
```
Now you will be pushing your file to github using below command
```
git push -u origin main
```
Now add some more changes to the READMD file, and commit
```
git commit -am "Updated READMD.md file"
```
Now push
```
git push
```
Now, go to github.com and edit your READMD.md and make some changes. Then come back to terminal, and type
```
git pull
```

This should pull the changes you made directly in github wehsite.

If you are working on this file and you haven't made any commits but you wish to restore this file back to as it was, you can use the following command.
```
git checkout -- README.md
```
Try making some changes but do not commit. And then run the above command. The file will reset to it's original state.

Now try to do some unnecessary changes and push the file again.

Previously we tried resetting the file locally. Now we will revert the commit itself. After pushing the file, use the following command
```
git revert HEAD
```
This should revert the commit and your changes are gone. This will keep the history clean as well.

Now to revert but keep your changes staged you can use the soft reset command
```
git reset --soft HEAD~1
```
This should reset your last commit but keep the changes staged (git add stages the changes)

To revert the changes as well as unstage them use the mixed flag instead of soft
```
git reset --mixed HEAD~1
```

To revert the changes as well as delete them entirely, use the hard flag instead of mixed
```
git reset --hard HEAD~1
```

Now let's create a branch. To create a branch, use the checkout command.
```
git checkout -b feature/readme
```
```feature/readme``` is your branch name

Now make some changes and commit
```
git commit -am "Updated feature/readme"
```

Now go to main branch
```
git checkout main
```
Now merge ```feature/readme``` into main using following command
```
git merge feature/readme
```
Once done, basically you have merged your branch locally. Now you can do git push to push the changes
```
git push
```

Then let's delete the branch
```
git branch -d feature/readme
```
This will delete the branch.

Now make some changes in your readme file and then we will stash it using below command
```
git stash
```
Stashing saves your changes without commiting them. You can restore it later. You use this command if you wish to switch between branches without commiting or any other case.

Now to restore the stash, use the below command
```
git stash pop
```

This should restore your changes and then you can push those.

Now, in the terminal type
```
git log
```

This should show you a log of commits that happened on your branch. to see more you can press the down arrow which will let you scroll down. To exit, press the ```q``` key.

To see the logs in a better way, you can add flags like following
```
git log --oneline --graph --all
```
The ```oneline``` flag will show you each commit with message in one line. The ```graph``` flag creates a graph of branches to the left. The ```all``` flag should show all commits.

Now, make some changes in the README.md file and then use following command:
```
git diff
```
This command will show current changes that aren't yet committed.

Now, make some changes in the README.md file and then check the status of the commits using following command
```
git status
```
This will show you the changes that are staged or not staged, committed or uncommitted, everything.

Now let's talk about rebasing. 

Imagine you are working on branch1. someone merged some changes in main branch. You need those changes in branch1. So you merge main into branch1.

Now, if this happens multiple times, you will have multiple merges in your branch1.

If you finally merge branch1 into main, the main branch history will show multiple merges from main to branch1.

![image](/assets/image1.png)

For a cleaner approach, instead we can rebase. Rebasing in simpler words is instead of merging you simply put

yx

That's all.

## If You Don't Have Git Configured

Download git for windows [here](https://git-scm.com/downloads/win) 

Download git for mac [here](https://git-scm.com/downloads/mac) 

Download git for other platforms [here](https://git-scm.com/downloads/linux) 


Use the below commands to configure your infomration for all repositories
```
git config --global user.name "<full name>"
git config --global user.email "<email>"
```

