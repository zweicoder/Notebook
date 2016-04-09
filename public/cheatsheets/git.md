# GIT
### Merging Pull Request
`git fetch origin pull/id/head:name`
> Where id is the pull request id, head is the remote branch (on the fork), and name is the name you want to give the local branch.

`git pull https://github.com/otheruser/repo.git branchname`


### Checking out upstream
Fetch upstream
`git fetch upstream`

Create and switch to a local version of the new upstream branch:
`git checkout -b newbranch upstream/newbranch`

When you're ready to push the new branch to origin (and track it):
`git push -u origin newbranch`

### Push without history
Checkout branch with no history, then commit and push
`git checkout --orphan `

or if no one is working on the repo,
`git push -f origin orphan:master`

### Change remote
`git remote set-url origin `

### Rename branch
`git branch -m  `

### Force add ignored file
`git add --force my/ignore/file.foo`
