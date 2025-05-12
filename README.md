# Git Practice Repo

Learn with me...

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

Preparing to reset hard