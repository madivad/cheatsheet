# git—Cheatsheet by Madivad
*I'm new to git and h*

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





    git log --oneline --decorate --all --graph
