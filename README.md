# MacOS Git configuration and basic usage

## Install [Homebrew](https://brew.sh)
  Homebrew is a package manager for MacOS.  It installs packages to their own directory and then symlinks them into /usr/local. 

The following commands should be run as your local user (not sudo'd to root) in your terminal

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

## Install git 
```
brew update
brew install git
```

## Global configuration
Configure your global settings:

```
git config --global user.name "Your Name"
git config --global user.email "<yourname@youremail.com>"
```


## SSH Key Creation 
SSH Keys allow for secure communication when pushing or pulling code from a remote repository, such as github.com

  (only necessary if you don't already have a set of keys that you would like to use)

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

## Add the new key to your github account
1) Copy the contents of ./ssh/id_rsa.pub and paste into the appropriate form in your git website personal settings

  [Adding the new key to your github account](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)


---
# Git Usage
[Git Documentation](https://git-scm.com/docs)

## Generic git flow
1. Create the new repository from within the web interface
2. Clone the new repo to your local working directory
3. Create/Add your code inside the newly created repo directory
4. Be sure to add a README.md file to describe the contents/state the purpose of the repo
    1. [Basic markdown cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
5. Don't wait to commit!  Each commit should be one minor update to the code, not an entire re-write
    1. Add the files in the local repo: 
	```
	git add .
	```
    2. Add a descriptive commit message
	```
	git commit -m "Updated the foobar function to properly sanitize input"
	```
    3. Push the code to the remote
```
git push
```
       1. The first time you push code, you must specify the remote origin and branch
```
git push -u origin master
```

6. Branching should be used on code that has been published! (never push directly to master unless you are the only one working on the code, and even then, it's not recommended.)
    1. Create a new branch and name it after the specific fix or enhancement.
        ```
	git checkout -b "jira_or_feature_name"
	```
    2. make your updates to the branch as specified in #5 above
    3. push the code and create a merge request immediately
```
        git push
        git merge "jira_or_feature_name"
```
    4. or to invite peer review, you can create a merge request from the web gui
    5. depending on your workflow, either the peer will merge the code, or they will approve it so that you can merge it.
    6. [Git Branching](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)

## Basic commands
* git status
* git diff 
* git log
* git commit -m "descriptive message"
* git pull
* git fetch
* git push
* git clone <git repository url>
* git checkout -b "feature_name" 
* git merge "feature_name"
* git branch "branch_name"

## Create a new repository
```
git clone git@git.yourcompany.com:your_git_username/your_repo_name.git
cd your_repo_name
touch README.md
git add README.md
git commit -m "add README"
```

## Push an existing folder
The remote repository must be created on the server first (via the web interface)

```
cd existing_folder
git init
git remote add origin git@git.yourcompany.com:your_git_username/your_repo_name.git
git add .
git commit -m "Initial commit"
git push -u origin master
```

## Push an existing Git repository
The remote repository must be created on the server first (via the web interface)

```
cd existing_repo
git remote rename origin old-origin
git remote add origin git@git.yourcompany.com:your_git_username/your_repo.git
git push -u origin --all
git push -u origin --tags
```
Last Updated: Sun 10 May 2020 11:24:51 AM CDT
