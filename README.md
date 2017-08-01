# git cheatsheet
*I'm new to git and github and I found that most online tutorials were either too basic or too complicated. I don't want to be just told how to do something, I want to understand WHY it is that I am doing something this way. So this is what I have learned after 2 days of youtube, stackexchange and general experimentation. I hope this help you, Cheers.*

## Just show me the commands:
*I was going to put this at the end, but then again, I'm probably going to come back to this page a bit and I'm going to not want to scroll down either:P*

    git log --oneline --decorate --all --graph

this will be your favourite log command. it provides a colourful ascii art tree of the current project.

    git status                  # just that, what's the current location and file status
    git branch -a               # show all branches
    git branch {new-branch}     # create a branch named {new-branch}
    git branch -d {branch}      # delete branch
    git branch -D {branch}      # force delete branch
    git branch -rd {branch}     # delete remote-tracking and local branch (but not origin branch!)
    git push origin -d {branch} # delete remote branch. This includes above remote-tracking branch
    git checkout {branch}       # checkout (or into) {branch}
    git add {file}              # adds a file to the next commit
    git commit                  # commits current staged changes (prompts for commit msg)
    git commit -a               # performs an add and a commit at once
    git commit -am "msg"        # performs add, and commit with {msg}
    git push origin {branch}    # pushes your {branch} to origin
    git remote add {alias} {url} # adds {alias} (usually origin) for remote {url}
    git remote -v               # verify or show me the remote aliases
    git fetch origin {branch}   # pull and merge origin branch to local
    git pull origin master      # pull origin and update local master branch


## Terminology:
### git clone:
In the beginning there was cloning. You begin a clone with `git clone {remote-repo}` (examples at the end of this page). This created a copy of the repo locally for you to play with.
### Unstaged Changes:
Changes to files that are not committed to be updated. Whilst working on these files you will be unable to change to another branch without either committing the changes or stashing them.
### Staged Changes:
Changes to files that have since been added to the commit phase, but not yet pushed to the remote repo
### pull:

## I see there are THESE starting points:
1. You have your own local repository (repo) and *local remote* \* repo. This is a great starting point for experimentation.
1. You have your own repo (repository) on github and you want to continue doing some development on your local machine
1. You have a project on your local machine and you want to put it up on github and manage it from there
1. You have downloaded a repository (repo) from github and you've experimented with it. You now want to make some changes

\* *a "local remote" is a remote repo that is local to you on your computer or your own network. I used a local remote to do a lot of testing on this and to really get a grasp of what was actually going on.*

# 1. Scenario: All local
We're going to write a quick bash script that (for whatever reason) you want to manage through a local git repo. We're going to look at this as if we've already started work on the file and we're now going to add it.

\* *The current working directory should only contain files pertinent to your project. If it contains any other projects or files, you'll need to create a specific directory for it. Not necessary, but I now have a `git` folder with each of the projects listed under it.*

this is our file:

    ~/git/my-awesome-script/hello-world.sh

# 2. Scenario: download and work on a remote repo
*my first forks were legit forks, however my recent stabs at nodejs have seen me clone a few repos straight to my computer and make changes. I now want to work on those changes and post to my github. Because I don't feel my "experimentation" is worthy of a pull/push into the original project, I am creating my own project. This is the workflow:*

This scenario begins with an initial clone

----


## Start a local repo and want to push it up online to git
## Fork a repo from someone else's git
## Bring your own repo to local (and make changes and upload)
*an example of this is you have a repo online from a previous install or from another computer. You want to start working on it again*
* first, clone it to local  
`git clone {repo-details}`  
eg:  
`git clone https://github.com/madivad/project.git`

* change into the directory (`cd {project}`)
* make your edit or add your file

If you added a file, `add` it to the repo:  
`git add {filename}`

Commit your new/edited file to the local repo:  

    git commit {filename} -m "{commit message}"
    git push
    git rebase master {branch}  #<< Yeah, I didn't checkin





# Create a new repo from the command line
* *from what I've been able to work out, you can't COMPLETELY create a repo from the command line, you must at least START the process on github itself.*
* *start in the working directory of your project*
* *this can be an existing unmanaged project or a new project*

### on your github page:
1. click the plus sign in the top left corner and select `new repository`.
1. give the repository a name (required), a description (optional), select between public or private (private is a paid feature), and **DO NOT** `initialize this repository with a README`. Also, do not add a `.gitignore` or license from this screen.
1. click `Create repository`

### back in your working directory:

1. If you don't have a `README.md`, create one:

    echo "# {ProjectName}" > README.md

2. then:


    git init
    git add .
    git commit -m "first commit"
    git remote add origin https://github.com/{user}/{project}.git
    git push -u origin master

3. If you already have a managed project in your project folder (you probably won't be reading these instructions), then:


    git remote add origin https://github.com/{user}/{project}.git
    git push -u origin master

---

# `remote` repos and `origin` what are they?
This one wasn't immediately obvious to me.

When you add a remote `origin` you are adding an alias to make the whole process of management that little bit easier.

### First add origin to the repo
What we are really doing is creating a local alias for a remote repo.

    git remote add origin https://github.com/{user}/{project}.git

You can verify the remote alias by typing: `git remote -v`

    $git remote -v
    origin	git@github.com:madivad/cheatsheet.git (fetch)
    origin	git@github.com:madivad/cheatsheet.git (push)


`origin` is a local alias for a remote repository. Now instead of pushing to your remote repo via a URL, you can simply `push origin master`:

Before:

    git push https://github.com/{user}/{project}.git master

After:

    git push origin master

Just remember, origin (in this instance) is located on github by virtue of the `remote add`.

Next, let's make authentication wasier.

# Add SSH key to github
As long as your PC is secure, adding an SSH key to github makes authentication much easier.

* Go to your avatar in the top left corner,
* Click on settings,  
* Go down to SSH and GPG keys.
* Add your PUBLIC key here.

Now when pushing commits to github you will no longer be asked for your credentials.

# Other little tidbits
### one line colourful log art :)

    git log --oneline --decorate --all --graph

### Git commands to remote github can be either by `HTTPS` or `SSH`:

    git clone git@github.com{user}/{project}.git
    git clone https://github.com/{user}/{project}.git

## `git pull` = `git fetch` and `git merge`
### first: git clone
`git clone` will clone a repo from github into a directory named after the online project. ie:

    git clone https://github.com/madivad/cheatsheet.git

will create a directory called: `cheatsheet`

    $ls -al cheatsheet/
    total 20
    drwxr-xr-x 3 user group 4096 Date 1 13:34 .
    drwxr-xr-x 3 user group 4096 Date 1 13:34 ..
    drwxr-xr-x 8 user group 4096 Date 1 13:34 .git
    -rw-r--r-- 1 user group 4113 Date 1 13:34 README.md

What it also does is sets up a remote origin to that project. This comes in handy later.

    $ cat cheatsheet/.git/config
    [core]
      repositoryformatversion = 0
      filemode = true
      bare = false
      logallrefupdates = true
    [remote "origin"]
      url = https://github.com/madivad/cheatsheet
      fetch = +refs/heads/*:refs/remotes/origin/*
      [branch "master"]
      remote = origin
      merge = refs/heads/working

### git log, git status

    git status          # just that, what's the current location and file status
    git log --oneline --decorate --all --graph

this will be your favourite log command. it provides a colourful ascii art tree of the current project.


### git branch:

    git branch -a               # show all branches
    git branch {new-branch}     # create a branch named {new-branch}
    git branch -d {branch}      # delete branch
    git push origin -d {branch} # delete remote branch
    git checkout {branch}       # checkout (or into) {branch}
    git add {file}              # adds a file to the next commit
    git commit                  # commits current staged changes (prompts for commit msg)
    git commit -a               # performs an add and a commit at once
    git commit -am "msg"        # performs add, and commit with {msg}
    git push origin {branch}    # pushes your {branch} to origin
    git remote add {alias} {url} # adds {alias} (usually origin) for remote {url}
    git remote -v               # verify or show me the remote aliases


# THE END
