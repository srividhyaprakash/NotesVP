git add . - Add all files that were changed
git add <filename1> <filename2> - Add those files you have mentioned 


git commit - commits the file - stages the file. You need to write a message. 
git commit -m "Message goes here" - write the message inline 
git commit --amend -m "New commit message goes here" - Command to change the commit message. Do this only if you have NOT pushed to the remote repository already. 

Always do a pull before pushing on to the remote repo

git pull origin master
git push origin master


git diff - Shows all the modifications that are not committed across all the files

git status - Shows the status of all the files, whether they are untracked, tracked, modified.

Dealing with branches:

git branch <branchname> - Just creates the branch, doesn't switch control over to the branch

git checkout <branchname> - Transfers control to the branch

git branch -a - Lists all the branches


Pusing a branch onto the remote repository:

git push -u origin <branch-name>



git cherry-pick <first 7-8 alphanumeric values of the hash> - Copies whatever work was done in the master or wherever this hash was committed to the current branch.

git reset --soft <first 7-8 alphanumeric values of the hash>
git reset --hard <first 7-8 alphanumeric values of the hash>
git reset --mixed (default)


Merging a branch:

1. Be in master and pull all changes. 
2. git branch --merged - Branches that have been merged so far (Used more for keeping track)
3. git merge <branchname> - Merge the branch on the master
4. git push origin master - Push the master to the remote repo
5. We still need to delete the branch from the local repo and the remote repo. 



Deleting a branch: 

git branch -d <branchname> - Delete branch locally
git push origin --delete <branchname> - Delete branch remotely



git clean -df - Clean up and not commit all untracked files


git log - shows you a history of all the commits with their hash so far


git revert <first 7-8 alphanumeric values of the hash> - Creates a new commit on top of the all the existing commits, rolling back to the version that the hash indicates. This prevents history corruption with all other colloborators of the remote repository.


git stash save "Meaningful description of what you are saving." - Saves the modified work and just treats as though nothing has been modified. Useful tool to copy the work from one branch to another. Kind of like stack. Once you do a git stash, go to the other branch 


git stash list - Lists all the stashed work 

git stash pop - Pops the first item in the stack and applies those changes in the current branch.


git stash drop <entire stash index> - Drop the first stash in the stack
example: git stash drop stash@{0}


git stash drop - Drop all the stashed work 


git reflog - Every activity we have done so far with respect to this repository. 


OSS workflows

Contributing to OSS

1. Fork the project.
2. Clone the forked repo. 
	git clone <forked-repo-link>
3. create a branch. 
	git checkout -b <branch-name>
4. Work on the branch
5. Commit the branch to forked repo.
	git add .
	git commit -m "Message"
	git push origin <branch-name>
6. Create a pull request.
7. Wait for it to be accepted. 
8. Done.


Deleting local branch and remote branch once pull request accepted.

1. Go to master branch in local repo.
	git checkout master
2. Merge the local branch onto local master
	git mergre <branch-name> master
3. Delete the local branch
	git branch -d <branch-name>
4. Delete the branch from remote repo
	git push origin --delete <branc-name>


Syncing your forked repo with the original repo.

1. Add upstream of the original repo
	git remote add upstream <original-repo-link>
2. Fetch the upstream repo to your local repo
	git fetch upstream
3. Checkout local master
	git checkout master
4. Merge local master with upstream master
	git merge upstream/master
5. At this point, your local master is in sync with the master of original repo, 
	but not the forked repo (i.e your remote repo)
6. To do so, 
	git push origin master.




