# Git Practice Repo

Learn with me...

This is a tutorial for git commands. This should give you a basic idea of each git command specifically for interview preparation.

This tutorial assumes that you already have git installed and configured.

### Basics
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

### Resetting Unstaged Commits
If you are working on this file and you haven't made any commits but you wish to restore this file back to as it was, you can use the following command.
```
git checkout -- README.md
```
Try making some changes but do not commit. And then run the above command. The file will reset to it's original state.

Now try to do some unnecessary changes and push the file again.

### Reverting Pushed Commits
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

### Stashing

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

### Logging
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

### Now let's talk about rebasing. 

Imagine you are working on branch1. someone merged some changes in main branch. You need those changes in branch1. So you merge main into branch1.

Now, if this happens multiple times, you will have multiple merges in your branch1.

If you finally merge branch1 into main, the main branch history will show multiple merges from main to branch1.

![image](/assets/imge1.png)

The above looks messier and harder to read.

For a cleaner approach, instead we can rebase. Rebasing in simpler words is instead of merging you simply copy main branch history into branch1 history and place branch1 history above the main copied history.
![image](/assets/image2.png)

The above is much cleaner to read.

Let's mimic this.

#### Merge Flow
in your main branch, create a file main.txt, write something in it, and then save it and commit main branch with message 
```
git commit -am "Main Commit 1"
```
Now create another branch 
```
git checkout -b branch1
```
Create a file branch1.txt, write this in it:
```
Branch Commit 1
```
And then save it and commit branch1 with message
```
git commit -am "Branch Commit 1"
```
Then go to main branch
```
git checkout main
```
Make some changes in text1.txt and commit
```
git commit -am "Main Commit 2"
```
Now go back to branch1
```
git checkout branch1
```
To merge main -> branch1, we will write
```
git merge main
```
Then we will make some changes in branch1.txt, and then commit
```
git commit -am "Branch Commit 2"
```
Then go to main branch
```
git checkout main
```
Make some changes in text1.txt and commit
```
git commit -am "Main Commit 3"
```
Now go back to branch1
```
git checkout branch1
```
To merge main -> branch1, we will write
```
git merge main
```
Then we will make some changes in branch1.txt, and then commit
```
git commit -am "Branch Commit 3"
```
Now go to main branch and merge branch1 into main
```
git merge branch1
```
Now if you try to log the main commits using following command
```
git log --oneline --graph
```
Observe the graph and the commits, those will look cleaner than the merge.

To see how merge commits would look, all you need to do is write ```git merge main``` instead of ```git rebase main```.

#### Rebase Flow
in your main branch, create a file main.txt, write something in it, and then save it and commit main branch with message 
```
git commit -am "Main Commit 1"
```
Now create another branch 
```
git checkout -b branch1
```
Create a file branch1.txt, write this in it:
```
Branch Commit 1
```
And then save it and commit branch1 with message
```
git commit -am "Branch Commit 1"
```
Then go to main branch
```
git checkout main
```
Make some changes in text1.txt and commit
```
git commit -am "Main Commit 2"
```
Now go back to branch1
```
git checkout branch1
```
To rebase main -> branch1, we will write
```
git rebase main
```
Then we will make some changes in branch1.txt, and then commit
```
git commit -am "Branch Commit 2"
```
Then go to main branch
```
git checkout main
```
Make some changes in text1.txt and commit
```
git commit -am "Main Commit 3"
```
Now go back to branch1
```
git checkout branch1
```
To rebase main -> branch1, we will write
```
git rebase main
```
Then we will make some changes in branch1.txt, and then commit
```
git commit -am "Branch Commit 3"
```
Now go to main branch and merge branch1 into main
```
git merge branch1
```
Now if you try to log the main commits using following command
```
git log --oneline --graph
```
Observe the graph and the commits, those will look cleaner than the merge.

#### For interactive rebasing
you can use an extra flag ```-i``` like below
```
git rebase main -i
```
This will open up an editor with instructions allowing you to make changes allowing you to squash or pick commits. Squashing is combining multiple commits into one.

### Alias

You can create alias for commands to make them shorter
```
git config --global alias.st status
```
So next time, you will be calling status command using
```
git st
```
### Renaming a branch locally
You can use the following command
```
git branch -m master main
```
In the above example, we are renaming our current branch on local i.e. master to main.

### Unrelated Histories
If you ever encountered issue regarding pulling a git branch but it gives error regarding "unrelated histories", you can use the below command to pull ignoring unrelated histories
```
git pull origin <branch>  --allow-unrelated-histories
```

That's all.
