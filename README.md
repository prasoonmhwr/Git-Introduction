# Introduction to Git

In a nutshell, Git is a distributed source-control or version-control system which helps in keeping track of the changes in source code and also helps developers to coordinate during any software development. To read more about it's origin, design, developers, etc., you can go to this [wikipedia link to git](https://en.wikipedia.org/wiki/Git "wikipedia link to git")

### Topics

* [Git Installation](#Git-Installation "Goto Git Installation")
* [Basic Git Command](#Basic-Git-Command "Goto Basic Git Command")
* [Branching](#Branching "Goto Branching")
* [Stashing](#Stashing "Goto Stashing")
* [Tagging](#Tagging "Goto Tagging")
* [Rebasing](#Rebasing "Goto Rebasing")
    
## Git Installation

Git installation is pretty straight forward.

__On Windows__

You just have to download the installer from [git-scm.com](https://git-scm.com/ "git-scm.com"), and then run it, thats it. Git will be installed.

__On Mac OS__

If you have XCode installed on your MAC then you do not need to do anything, git will already be there, if not then you have to just run command "__git version__" in your terminal and MAC will prompt you to install either XCode or command line developer tools, you can choose to install just command line tools if you dont want to install XCode. 

## Basic Git Command

__git init__

> Create an empty Git repository or reinitialize an existing one

`git init`

As mentioned in the blockquote above this command is use to initialize the git repo. So basically you can use it for different scenarios.

- While creating new project

Just type the below command in your terminal/command prompt

`git init project-name  //you can replace project-name with your own project name`

2. Reinitializing the existing project

For this scenario you have to first navigate to your project folder, then just type git init.

```cd project-name 
git init
```

__git status__

> Get the working tree status

This command gives the information about the status of working tree compared to git repository. Type the command:

`git status`

and you get information something like below image.

![picture alt](resources/images/status.png "On running git status")

As you can see in the image above, it shows two types of files one is tracked and other is untracked.
Tracked files are those which git is already aware of and are just modified. Untracked files are those which are newly added and git is not keeping track of it.

One more thing to notice in above image is the line "__Your branch is ahead of origin/master by 1 commit__", this is the summary of the current status of the working tree with respect to git repository.

git add

git commit

basic git flow/first commit, introduce git pull, git push

git clone

adjusting the config with git config

Express commit

git reset

renaming with git mv filename1 filename2

removing file with git rm filename

history

git log
    git log abbrev-commit
    git log --online --graph --decorate
    git log indexM...indexN
    git log --since="3 days ago"
    git log -- sample.txt
    git log --follow -- some.txt

git show

Alias
    git config --global alias.hist "log --all --graph --decorate --oneline"
    git hist

adding .gitignore

## Branching

## Stashing

## Tagging

## Rebasing

