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






