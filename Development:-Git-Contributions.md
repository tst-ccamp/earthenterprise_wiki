# Managing Your Repository

## Establishing SSH Key
Before beginning, you will first need to make sure that an SSH key has been generated for your account, and that the key exists locally as well. This can be accomplished by following instructions mentioned here: https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/

If this is not in place, you will experience permissions errors when cloning and pushing.

## Fork and Clone
To work with your own copy of GEE, you will first need to create a fork. From the main GEE github page (https://github.com/google/earthenterprise) click the Fork button in the top right. Once the fork has completed you will then need clone the repository. Lastly, you will need to configure the upstream repository for receiving and creating updates.
 
```
git clone git@github.com:<username>/earthenterprise.git
// move into the repository directory  
cd earthenterprise  
// set the upstream  
git remote add upstream git://github.com/google/earthenterprise.git
```

 
## Keeping your fork up to date
It is important to always keep your fork up to date with what is in the master repository. This will make life much easier when trying to push your issue branches.
 
```
git checkout master
git fetch upstream
git pull upstream master
git push
```


## Issue Branches
When you’re ready to work on a new issue create a branch in your cloned repository.
 
First, update your fork as mentioned above. Then create your branch. You can optionally add the '-t origin/master' for tracking:
 
`git checkout -b branch_name [-t origin/master]`

You are now on your shining new feature branch for development.

## Making Contributions

### Creating a Commits
When creating a commit message please include the issue number so that git will autolink to that issue. In addition, the commit message should contain a concise description of the change in this branch. 
 
`Replaced all fizzbars with foobars. Unit test fixed per issue request (#102)`
 
### Pushing your commit
Make sure git user.name an user.email are configured correct. This must be the email used to sign up the [CLA](https://cla.developers.google.com/clas)

`git config --global user.name`  ( also can be changed to `--local`, depending on your preference)

`git config --global user.email`

When you are ready to commit your change to your forked repository, do so with a git push.
 
`git push origin branch_name`
 
If you are ready to create a pull request to master, go to your forked repository’s github page and select the appropriate branch in the branch dropdown. To the right, under the clone button, a “pull request” label will appear. Click this to start the pull request process. Perform a sanity check on the number of commits and the files changed before creating the pull request. Add a description with the following info into the request description box: 
* A concise description of the change being made
* Reproduction steps for testing the fix
* Operating System(s) tested on
* A “Fixes” line for each issue this change is fixing Ex: 
* Fixes #12
* Fixes #13

Then click the big green button and your pull request is on the way!

