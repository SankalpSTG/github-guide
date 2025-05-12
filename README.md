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

