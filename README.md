This project is created for study purpose to understand GIT using git bash and remote github repository management.

We will try to understand basic commands to manage our local project and push it to remote repository.

As I am working on react projects, so for starter we will create a react app using a command --> npx create-react-app yourProjectname

This will create a basic react app with all the pre-requisite configuration needed to start with. Interestingly it also created a .git file which indicates it is a git repository.

To check whether it is git branch , try running --> git branch and it will list you all branched within this local repository.

Once we created our project, try to make some changes to local files and commit those changes so that you can get familiar with git bash and its command.

You can either use notepad++ or vscode for git editor.
You can choose it while installing git from https://git-scm.com/ .
You can also manually add notepad++ as your default editor using command
First create or update ~/.bash_profile inside home directory.
command in git bash --> notepad++ ~/.bash_profile . Add a line inside this file.
alias npp= 'notepad++ -multiInst -nosession' . Save and close.
Next command --> git config --global core.editor "notepad++ -multiInst -nosession".

Test GIT notepad integration using --> git config --global -e. It will open in notepad++.

## Next , I am using P4Merge tool to compare the differences and merge files.
Go to perforce.com- download P4Merge : Visual Merge Tool. While installing only install P4Merge tool, uncheck other checkboxes to install other applications.

Go to Program files and check for Perforce folder and copy the path.
## Steps to setup diff tool to git.
command --> git config --global diff.tool p4merge
command --> git config --global difftool.p4merge.path "C:/Program Files/Perforce/p4merge.exe"
command --> git config --global difftool.prompt false

## Steps to setup merge tool to git.
command --> git config --global merge.tool p4merge
command --> git config --global mergetool.p4merge.path "C:/Program Files/Perforce/p4merge.exe"
command --> git config --global mergetool.prompt false

## Hurray!!! git integration with notepad++, and p4merge is completed. Now you can start editing files and commit your changes to local repository.

Try to make some change to README.md file for demo.
To check the current status of the branch . Run --> git status.
It will show the modified file/s in red which are unstagged.
To stage the file/s. Run --> git add fileName or git add . --> to add all files to stage area.
Now you can run --> git status and it will list down files in staged area in green color.
Once it is in stage area , you can run --> git commit -m "you message".

Express commit command - to directly stage and commit. Run --> git commit -am "your message".

You can also go back to previous point , if you want to go back-
Run --> git reset HEAD README.md --> git checkout --README.md
 
Using git log command , you can view all history but on git bash it is little congested and not easy to understand. We can format the log output in a more cleaner way.
Run --> git config --global alias.hist "log --oneline --graph --decorate --all"
Now Run --> git hist -- hist is your create alias. It can be named anything you want.

To check the differences between local and head version. we can do this with our difftool.
Run --> git difftool commitID HEAD

You can also add a feature branch to your master branch to work on different app features or anything.
To create a new branch -- git checkout -b branchName.
This will create a new branch and switched you to the newly created branch.

Now to go back to master. Run--> git checkout master
To merge other branch to master branch --> git merge branchName.
This type of merge is called fast-forward merge.
Now if you want to delete the branch. Run --> git branch -d branchName

If while merging there is any conflict - Run --> git mergetool.
It will open p4merge with windows - your changes, changes on master, changes on other branch if present. Select the version you want .select and save and close p4merge.

Next -  git commit -m "Resolving conflicts"
Now when you run git status - you can find one file with .orig extension. which is the original version of that file.
You can mention .orig extension inside .gitignore file to now show such files for commiting. optionally you can also delete this file.

GIT STASH --> use to save our modified files to stash so that we can commit it later whenever we want.
RUN --> git stash
To view stash files. RUN --> git stash list.
To bring back stashed file. Run --> git stash pop.

## Hurray!! We have now learned all basic commands. I will add if anything is missed. So keep track of this file.

Now we will link our local repository with our github.
I will assume you do have a github account if no then create one. It is very simple.
Now click on plus icon on top right besides your profile icon.
Create a new repository. Give your repository name and leave rest of the fields as it is.

Now go to you project folder in local and run following command.
--> git remote add origin "your github path.git" 
## you can find this changes while creating a repository on github.
## To push our files to remote. Run following command.
--> git push -u origin master
