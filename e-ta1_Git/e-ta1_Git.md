---
title: "e-TA 1: Version control with Git(Hub)"
author: 
  name: "Ignacio Sarmiento-Barbieri & Jacob Muñoz Castro"
  affiliation: "Universidad de los Andes | [ECON 4676](https://github.com/ECON-4676-UNIANDES)" 
output: 
  html_document:
    theme: paper
    highlight: haddock
    # code_folding: show
    toc: yes
    toc_depth: 4
    toc_float: yes
    keep_md: true
---




Hello! Welcome to e-TAs, your on-line help for ECON 4676. So you want to learn how to use Github. In this Lab you will learn the intricacies and specifics of working with Github, as well as strategies to keep your file version control under your control. The present issue focuses on the basic operations of `Git` and `Github`. The core material was extracted from tutorials at the [BDEEP group](https://www.uiuc-bdeep.org/about) at [NCSA](http://www.ncsa.illinois.edu/site) and [Grant McDermott](https://grantmcdermott.com/) tutorial at the University of Oregon e-TA's. [^fn-1] 


[^fn-1]: If you have comments, suggestions, etc. please submit a pull request ;).





## Repositories

When you begin a new coding project, you will want to create a new repository. This repository will grow to hold all of the important files for your project. 

### Create a repository
You can create a new repository by clicking the green "new repository" button on your github homepage.

##### Step 1: Name your repository
Give your repository an accurate and concise name. You want the project to be recognizable! You can also add an optional description to summarize the goal of your project. 

##### Step 2: Public or private
Most repositories should be made public unless you have a specific reason to make it private. A public repository can be viewed by anyone but you can choose who can commit to it. Since it can be seen by others, it is possible to collaborate with others if you need help. A private repository can only be viewed by you and you are the only person who can commit to it, but you are able to manually add other collaborators as well. Private reposoitories are only available for paid accounts.

##### Step 3: Add a README
Finally, select "initialize with a README". You should only keep this unchecked if you are creating a repository from an existing repository. You can probably ignore the next two dropdowns: the gitignore dropdown allows you to choose any file types that will not be committed and the license dropdown allows you to select a license if you are sharing open source software.

Congratulations! Now you have created your own repository! In your repository, you can now add files by clicking "create new file" or "upload file" buttons to fill your repository with any files you will need. However, it may be easier to fill your repository with local files using your computer's command prompt. See the "Initialize a Local Repository" section of this tutorial for instructions on how to do that.



## Branches

Before we talk about version control, you need to understand branches. Branches are what github uses to ensure that there is always a working version of the code available for use. This fully functional branch is called "master". In order to make changes to master, you should create a branch off of it and make the changes in the new branch. Once you ensure that the code in your new branch is working perfectly, you can then merge your changes in the new branch into master (this is called a pull request). Once these changes are approved, the new branch that you created can be deleted and now the master branch will have the most recent version of your work. Here is a diagram of a normal github workflow:

<!--![](github_model.png)-->

#### Creating a branch:
Creating a branch is very simple to do. Just click the dropdown "branch" menu near the top left of your repository and type in a name for your new branch and then hit enter. Now the dropdown menu should contain the name of your new branch, but everything else will look the same because this branch is a clone of the master branch.

#### Pulls:
Pulls are used to "pull" a branch from github onto your local machine. If you have pulled the branch previously, it will merge any differences (such as if any files were added since your last pull). This is because pulling is actually a mixture of two git commands: git fetch and git merge, but git pull covers most use cases.Here is a visualization of a respository before a pull (courtesy of atlassian.com):

<!-- ![](bubble%20diagram-01.svg) -->

And this is what it looks like after a pull, as you can see the pull request is literally pulling the remote and local branch together into one vertex:

<!-- ![](bubble%20diagram-02.svg) -->

Pulling is accomplished through the terminal, so see the "Pull from a repository" section for steps to accomplish this. 

#### Commits:
Commiting a file means you are taking a snapshot of all files in a repository at a certain time. Every commit has an ID associated with it so that you are able to revert back to this snapshot of the code at any point in time. See the "Initialize a local repository" section for instructions on how to commit.

#### Pushes:
Commiting your code does not change any files in the branch you pulled from. In order to put these changes into effect in the online repository, you must push your code (after you have commited at least once). This sends your changes to the specified branch so that every future pull from this branch will contain the code that you just added. Before you push to a branch, it is always a good practice to pull from the branch so that any changes made by other users since your last pull will be added to your local copy. Once you ensure that your changes are still functional, it is safe to push your changes. Once again, the steps to accomplish are in the "Initialize a local repository" section.

#### Open a pull request:
If you are working with other collaborators, instead of pushing directly to master, you may wish to open a pull request. A pull request tells other collaborators that you are finished making changes to your branch and you want to apply these changes to master. Once you submit a pull request, other collaborators are able to view your branch and discuss your changes on a disussion board before the merge is accepted. Github will display your code by highlighting deletions from the previous version in red and highlighting additions in green. This is a very useful feature on team projects but it is unnecessary if you are the only one working in the repository. We will not go too in depth on pull requests in this tutorial.

#### Deleting a branch:
After a pull request for a certain branch has been approved and you no longer need to work on that branch anymore, it is safe to delete the branch. You can do this by clicking the "branch" icon here and then selecting the delete icon next to the branch that you want to delete. Make sure tht the branch says "merged" so that you know everything is up to date.

<!--![](delete_branch.png)-->


## Initialize a Local Repository:

Once you have a repository on GitHub, here is how you link it to your computer. This section is more code based side, with the specific commands you will need to use to get version control working for you!


1) First you want to start by opening up your command line tool, usually terminal.

2) Next you want to change your current working directory to the local project you want to uses version control on. Use the “cd” command to get to the directory of choice.

3) Once you are inside the chosen directory, type in: 

        git init
     
    This will initialize the chosen directory as a Git repository.

4) The next step is to use the command:

        git add ‘FOLDER’
     
     This command will stage the files in the folders mentioned for the next commit. This is the first step in adding files to Github. (Also “ git reset HEAD ‘FOLDER’ “ to un-stage the files for the next commit.

5) Next you want to commit your code with a short descriptor to differentiate files from one other. This is done by using the command: 

        git commit -m ‘commit message’
     
    The files are still not in your repository yet. (Also “git reset --soft HEAD~1” removes the commit, you will have to add and commit again)


6) After committing your files, you will want to push your files in to your remote repository. Before that though, we must specify which repository we are pushing to. This is done by running the command: 

        git remote add origin remote repository URL
    
    Then to verify that the repository exists/is valid run:
    
        git remote -v

7) Now everything is setup for a good push! Simply run this one last command:

        git push -u <remote_branch>
 
#### Here is a common code sequence you will use for pushing files onto your remote repository:

    git add folder_name

    git commit -m this is my commit message

    git push -u origin master

Here is what all of these commands will look like in your command line, sans the black lines.

<!--![](image--002.png)-->


### Revision Reversion:
And Wow! Now your code is in a remote repository! Congratulations! Make sure to practice good version control strategies by committing every major revision of your code with descriptive commit messages so you can revert back to different versions of your code using:

    git log

    git checkout “revision descriptor”

These commands together will print out a list of all of the versions and their information in your branch, and then simply add the revision descriptor of your choice into git checkout and you are set.



## Pull from a Repository:

Remember: when working with others, pulling is the best way to stay up to date with your group members’ latest revisions without even messaging them! 

Make sure you practice good version control strategies such as having multiple useful branches, and committing code with useful commit messages so there is no confusion.



### How to use Pull:

The actual command line command for common uses of git pull is:

    git pull <remote_branch>

This git pull version will grab all of the data in the remote branch, merges it with your local code, and then creates a new merge commit. It does not push the new merge commit. If you want to avoid staging a new merge commit entirely use:

    git pull —no-commit <remote_branch>


This is what pulling will look like. Look at all those files being merged...

<!--![](image--003.png)-->


