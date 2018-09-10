# Git Useful Cammands Reference

### Create New Repository, link it to Server and push contents to server

```sh
$ mkdir Repository_Name
$ cd Repository_Name
$ git init   #This will create the magical .git folder in this directory
```
Create, edit all files that you need to and when you want to commit these changes:
```sh
$ git add .
$ git status #to check which all files got added to the Repository
$ git commit -m "Some meaningful message for this commit"
```
>In case you miss out -m option, Vi editor will open up and please refer to [Vi Editor](Vi.md) to save your work & Exit Vi editor gracefully

If you Repository is not on the Server, you would need to create it on the Server by the same name (Repository_Name in this case) and get its URL reference, either HTTPS or SSH. Use the following command to add a remote reference to it so that you can push it to the server
```sh
$ git remote add origin git@github.com:rchidana/Repository_Name.git
$ git push -u origin master
```
>If you try to push without adding remote to it, the push would fail since there is no server configured to accept your push

### Check Remote exists or not and modify it if needed
```sh
$ git remote -v
origin https://git@bitbucket.org/anandr72/Test_Repo.git (fetch)
origin https://git@bitbucket.org/anandr72/Test_Repo.git (push)

#Remote is typically a URL to/from push/pull commits & changes; it is a short unique name for the identifier
#add remote
$ git remote add my-remote1 WHAT_EVER_URL.git
#show all remotes
$ git remote -v
#delete a remote by its name
$ git remote rm my-remote1
#rename remote
$ git remote rename old-name new-name
#change/modify remote URL
$ git remote set-url my-remote1 NEW_URL.git
#check details about a remote
$ git remote show origin
```
### Undoing Changes
Though Git has provisions to roll-back changes, it is always advisable not to go back in History unless & untill something is very critical.

#### Git Reset
This commands provides you 3 variations (Soft, Mixed & Hard) to un-do changes from Git History. Please refer to the following Git History of commits from a sample Repository, the top-most one is the recent commit and the bottom-most one is the first commit:
![](images/Reset.png?raw=true)

There are 3 ways to reset to any particular commit in History, say 4th Commit from the present one (as marked in the followed picture):
![](images/Reset1.png?raw=true)
* Soft Reset : Will un-do changes as per request but changes are retained and they are still present in Git Index
* Mixed Reset : This is the default option, and this is similar to Soft reset but the changes are removed from Git Index
* Hard Reset : Use this with caution as it will totally remove all changes that were made till that snapshot that is chosen

```sh
$ git reset --soft COMMIT_ID_OF_DESIRED_STATE
$ git reset --soft 9f1b24d6476af6304fd81a14096c6c243251a93b
$ git reset 9f1b24d6476af6304fd81a14096c6c243251a93b #Mixed Reset
$ git reset --hard 9f1b24d6476af6304fd81a14096c6c243251a93b #Will get rid of all changes this commit

$ git reset --soft HEAD^ #undo the last commit which typically rolls back one commit from the HEAD

$ git reset --soft HEAD^3 #Goes back 3 commits from the present Head
```

#### Git Revert

A better way of un-doing change is to add a new commit/change which un-does desirable change.This works on a commit by commit basis and can be applied for another number of commits, one after the other
```sh
$ git revert COMMIT_ID
# This will add a new commit (History goes forward) but this commit actually removes the changes done in COMMIT_ID
$ git revert COMMIT_ID1, COMMIT_ID2,... #A bunch of commits can also be taken care of one after the other but use this with caution
```

#### Git Commit amend

In case you want to modify the Commit message of the last previous commit, you can use this command to re-write the Git commit History:
```sh
$ git commit --amend -m "New Commit Message"
```
#### Git log, status and diff commands
```sh
# Log command shows the status of Git commits
$ git log
$ git log --pretty=oneline
$ git log --stat
$ git log --pretty=format:"%h - %an, %ar : %s"
$ git log --pretty=format:"%h %s" --graph
$ git log --since=2.weeks

#At any time, you can check the status of your Git Repository using status command
$ git status
$ git status -uno #Do not show untracked files

#diff command can be used to compare different versions of Git History
$ git diff COMMIT_ID_1 COMMIT_ID_2 #Shows all differences/changes between 2 commits
$ git diff master BRANCH_NEW #difference between two given branches
```
#### Git stash
At any point of Work in Progress, if you want to save your changes (not wanting to commit it as your work is not totally complete), you can use the stash command

```sh
$ git stash #saves your present work items with a stash number
$ git stash list #shows all stashes currently stored for you
$ git stash apply stash@{1} #Apply stash numbered #1
$ git stash pop #Pops and removes the top-most stashed work & applies it
```
#### Git Branches
Branching is a very cheap (in terms of resources) operation for Git, unlike any other version control systems where-in all resources get a new copy, and it is highly recommended to use as many as branches as required. Just ensure that you merge back the changes once your work is complete and prune/delete the un-required branch

```sh
$ git branch new_branch  #Will create new_branch from current branch
$ git checkout new_branch #Will change your current branch to new_branch
$ git branch -av #Shows all branches in your Repository

$ git push -u origin new_branch  #Pushing a new local branch on to the server

$ git merge feature_branch  #Merges feature_branch with current branch
#Delete a local branch
$ git branch -D new-branch #ensure that you are not on the branch which you are trying to delete
#Deleting a remote branch
$ git branch -rD origin/new-branch or
$ git push origin --delete <branchname>

#Pruning branches regularly so that your local branches are updated with server
$ git remote update –p
```

>Please note that there is no folder or directory that gets created for a branch, Git manages all branch information by playing around with File System snapshots

#### Git Tags
A Tag is nothing but another specific marker in Git History that can be used to highlight a specific milestone or release. There are two types of tags in Git, Lightweight and Annotated:

```sh

#Create a light weight tag
$ git tag v-1.0.4  #Creates a tag by name v-1.0.4 for present commit
$ git show v-1.0.4 #Shows details of this tag
$ git tag #Will show all available tags

#create an annotated tag
$ git tag -a v1.4 -m 'my version 1.4'
$ git show v1.4

#Tags need to be specifically pushed to the Server as & when needed
$ git push origin V1.4 #Push V1.4 tag to server
$ git push origin --tags #Push all tags in one shot

#Delete a specific Tag
$ git tag –-delete V1.4 
$ git push –-delete origin V1.4 #Deletes tag from the server

```

* [Git 101 Commands](Git101.md) 
* [Git Cheat Sheet](README.md) 
* [Vi Editor](Vi.md) 