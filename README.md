# git Cheatsheet

## Start a local repo and want to push it up online to git
## Fork a repo from someone else's git
## Bring your own repo to local (and make changes and upload)
*an example of this is you have a repo online from a previous install or from another computer. You want to start working on it again*


scratch notes here:

    git commit {filename} -m "{commit message}"
    git push
    git rebase master {branch}  #<< Yeah, I didn't checkin


    git log --oneline --decorate --all --graph



    `git clone https://github.com/madivad/project.git`

    git commit {filename} -m "{commit message}"
    git push
    git rebase master {branch}  #<< Yeah, I didn't checkin





    git log --oneline --decorate --all --graph

    git init
    git add .
    git commit -m "first commit"
    git remote add origin git@github.com{user}/{project}.git
    git remote add origin https://github.com/{user}/{project}.git
    git push -u origin master




    git remote add origin https://github.com/{user}/{project}.git


    Git commands to remote github can be either by `HTTPS` or `SSH`:


    git remote add origin git@github.com{user}/{project}.git
    git clone git@github.com{user}/{project}.git

    git remote add origin https://github.com/{user}/{project}.git

    # Add SSH key to github

    Go to your avatar in the top left corner. Click on settings and go down to SSH and GPG keys. Add your PUBLIC key here.


    # `remote` repos and `origin` what are they?
    This one wasn't immediately obvious to me.

    `origin` is a local alias for a remote repository. When you push to `origin`
    Now instead of:

        git push https://github.com/{user}/{project}.git master

    or

        git push origin master

    where origin is located on github
