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

You just have to download the installer from [git-scm.com](https://git-scm.com/downloads "git-scm.com"), and then run it, thats it. Git will be installed.

__On Mac OS__

If you have XCode installed on your MAC then you do not need to do anything, git will already be there, if not then you have to just run command "__git version__" in your terminal and MAC will prompt you to install either XCode or command line developer tools, you can choose to install just command line tools if you dont want to install XCode. 

## Basic Git Command

__git init__

> Create an empty Git repository or reinitialize an existing one

`git init`

As mentioned in the blockquote above this command is use to initialize the git repo. So basically you can use it for different scenarios.

__-> While creating new project__

Just type the below command in your terminal/command prompt

`git init project-name  //you can replace project-name with your own project name`

__->Reinitializing the existing project__

For this scenario you have to first navigate to your project folder, then just type git init.

```
cd project-name 
git init
```
Once you run this command a project folder is setup which contains __.git__ folder this folder keeps the track of the working tree's changes/activities.

__git status__

> Get the working tree status

This command gives the information about the status of working tree compared to git repository. Type the command:

`git status`

and you get information something like below image.

![picture alt](resources/images/status.png "On running git status")

As you can see in the image above, it shows two types of files one is tracked and other is untracked.
Tracked files are those which git is already aware of and are just modified. Untracked files are those which are newly added and git is not keeping track of it.

One more thing to notice in above image is the line "__Your branch is ahead of origin/master by 1 commit__", this is the summary of the current status of the working tree with respect to git repository.

__git add__

> Adding file contents to index/staging area

This command updates the index using the current content found in the working tree, to prepare the content staged for the next commit. Type the command:

`git add file_path`

Multiple file can be added by giving the filenames comma(,) separated.

`git add file1_path,file2_path`

or you can add all files together by using dot(.) in place of filename as:

`git add .`

![picture alt](resources/images/add.png "After running git add")

So if you run `git status` now you will see the files which were previously coming as not staged and/or untracked files in red color, are now coming as staged and ready to commit in green color.

What happens when we run `git add` is ,the "index" holds the snapshot of the content of working tree, this snapshot is taken as the content for the next commit.

Before running the commit command you can run this command as many times as you want , but after running the commit command if you run this command than content/changes will be staged for the next commit.

__git commit__

> Record changes to the repository(.git folder) but still in the local

This command creates a new commit containing the current contents of the index(the snapshot) and the given log message describing the changes. Just type the command:

`git commit -m "Log Message explaining the change"`

if you miss out giving the log message and just type `git commit` then git will prompt you to add a log message in the default editor configured with git. Now if you run `git status`:

![picture alt](resources/images/commit.png "After commiting your changes")

You can see that now our working directory is clean, our changes sits in .git folder which get created at time of `git init` . Still our changes are in the local , the reason is explained in the next topic below.

Another way of commiting is `git commit -am "log message"`, this technique is called __express commit__ using this you do not have to run `git add` but this only works for modified file, not for new file or untracked file, fot that you have to use git add. 

__Backing Out Changes__

Some times we accidently commit our changes or we do not want those changes , so we can reset our commit using command `git reset HEAD filename`. Let's understand this using an example, first we will add a test file named 'test.txt' using `git add .`, if we now run `git status` it will show our file in green as it is added:

![picture alt](resources/images/testAdd.png "Added test file")

if you the run the `git reset HEAD test.txt` it will be backed out to your working directory as shown below:

![picture alt](resources/images/reset.png "Rest test file commit/add")

now if you dont want the changes at all, all you have to do is run `git checkout -- test.txt`, this will revert the new changes.

__Basic git flow__

So let us now see the flow in a pictorial representation

![picture alt](resources/images/git_flow.png "Git Flow diagram")

As you can see in the diagram above , whatever command we have used so far keeps our changes in our local. In order to push your changes to remote repository you need to use `git push` we will see this command shortly before that we have to see how to configure a remote repo in our local.

__git clone__

> Cloning an existing repository into your local

This command helps us to clone the remote repo into our local, creates remote-tracking branches for each branch in the cloned repository (visible using `git branch --remotes`), and creates and checks out an initial branch that is forked from the cloned repository’s currently active branch.

After the clone, a plain `git fetch` without arguments will update all the remote-tracking branches, and a `git pull` without arguments will in addition merge the remote master branch into the current master branch.

> git pull - Fetching from and integrating with another repository or a local branch

Now while cloning you will be prompted to give you credentials for that repo. While pushing your changes, git by default takes the email you provided in your credentials and save it as you email and name. In order to change that you can adjust the config file with `git config`, all you have to do is type the command:

`git config --global user.name "Your Name"`
`git config --global user.email youremail@example.com`

this command can be used for configuring various other thing like defaut editor, merge tool,diff tool, etc. But that will be covered in this article.

Now to complete the git flow as mentioned we need to push to remote repo, in order to do that after running commit command you need to run `git push`.

__git push__

> Update remote refs along with associated objects

In technical terms it updates remote refs using local refs, while sending objects necessary to complete the given refs. In layman langauge it updates the repo with your changes. After commiting your changes into .git folder in local just type `git push`.

__Renaming a file__

It is always possible that sometime we misspell the file name, or want to rename for some other reasons, this can be done using the git command below:

`git mv filename1 filename2`

![picture alt](resources/images/renameGit.png "Renaming with git")

Now some of you might be wondering that we can always rename it using our operating system(Right click then rename), that is also fine but there is a small difference how git sees it. As you can see in the image above after you run the git command to rename, git consider it as a rename, but as you see in the image below when you rename using OS git consider it as deletion of file with old name and creation of new file with new name.

![picture alt](resources/images/renameOS.png "Renaming through OS")

__Removing a file__ 

Unlike renaming, removing a file is same either using git or using OS. So to remove a file through git you can use the following command:

`git rm filename`

__History__

> As the name suggest we will see how we can check our commit history/logs.

To start with just type `git log` and you see the logs of you commit in reverse chronological order, that means the top starts with last commit and we work backward in time as we go down.

![picture alt](resources/images/log.png "checking Log")

We can various other options to change the view of the log some of them are

`git log --abbrev-commit`

![picture alt](resources/images/abbrevlog.png "Abbrev log")

as you can see this will shorten the commit id, typically you need only 7 unique characters to identify your commit. The number of character increases as number of commits increses in your project.
    
`git log --oneline --graph --decorate`

![picture alt](resources/images/onelinelog.png "Online log")

Here --oneline will compress the entries in one line, --graph will provide the ASCII graph depicting the branching graph, --decorate will the labels or tags or anything which annotates our commits.

Another way we can see logs is using the commit number range, lets say from the image above we take c5eab45 to 6b89934, for that we type

`git log c5eab45...6b89934`

and as you can see in the image below it will show all commit between that range.

![picture alt](resources/images/rangelog.png "Range log")

Another option that we coould use with git log command is date base searching, so lets type

`git log --since="3 days ago"`

this will give log of commits happened in last 3 days. So consider you want to check log of a specific file for that run

`git log -- filename`

this will show all the commits having this file. Similarly if want to know the rename history of a specific file then type
    
`git log --follow -- filename`

here --follow gives the history of renames this file has gone through. You can refer to below image for quick example.

![picture alt](resources/images/followlog.png "follow log")

and finally

`git show`

> Shows one or more objects (blobs, trees, tags and commits).

this command show the information about a specific commit, lets say we want to check about commit number __cdde99a61ffb19e962a80e7a9e10182eb692b84d__ , type 

`git show cdde99a61ffb19e962a80e7a9e10182eb692b84d`

![picture alt](resources/images/showlog.png "show log")

This will give you all the information about that specific commit like author, date, what changes were made, etc.

__Alias__

Now lets say we want setup an alias(a short or different name for same work) for an very long command which we get bored of typing again and again. Let take an example from preivous command `git log --all -graph --decorate --oneline` typing this command again and again could be really frustrating and time consuimg so we can use an alias for this command for this we can use the command:

`git config --global alias.hist "log --all --graph --decorate --oneline"`

Now if you type `git hist` then it will return the same result as `git log --all -graph --decorate --oneline`.

![picture alt](resources/images/ "aliasing a command")

__Adding .gitignore__

One last thing before we move to the next section, we can also control which file should not be pushed or committed, files like log files or system specific configurational files and any other file which we want in the project but not in the repo, this can be achieved by adding __.gitignore__ file in your main project folder and inside this file we can specify which file we want to skip from committing, see the image below for an example:

![picture alt](resources/images/ "Adding .gitignore file")

## Branching

## Stashing

## Tagging

## Rebasing

