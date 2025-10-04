
### CONFIGURE GIT
`git config --global user.name name`
`git config --global user.email dat30581@gmail.com`
`git config --global core.editor "code --wait`
### MAKING NEW REPO
1. Initialize repo on local machine
`mkdir my_file`
`cd my_file`
`git init`

2. Clone repo
`git clone https://github.com/datdo-is-coding/my-note <another name>`

### ADD AND COMITTING CHANGES 
`git add <file_name>` add only one file
`git add .` : add all the files modified (add to staging area)
`git commit -m "message here"` : commit to repo

`git log`: logging of changes
`git log --oneline` : abbreviated version of log

### CREATING AND SWITCH BRANCH(ES)
`git branch` : return all branch(es)
`git branch <new_branch>`: create new branch

`git switch <new_branch>` : move to existed branch
`git checkout <new branch>` : move to existed branch

`git switch -c <new_branch>` : create and  move to new branch
`git checkout -c <new branch>` : create move to new branch

### MERGING BRANCHES
`git switch master`: move to the branch we want to merge
`git merge <new branch` : merge new branch to main

### CONNECTING TO GITHUB
`git remote add origin https://github.com/datdo-is-coding/my-note` : set origin

`git branch -M main` : select main

`git push -u origin main` : push changes to github
