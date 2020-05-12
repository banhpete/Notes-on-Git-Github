# Studying Git & Github
Just some notes on Git/GitHub based on https://www.ajonit.com/git/what-is-git/ & Kevin Skoglund's course on using Git/Github on Lynda. By no means is this a compehrensive guide on Git/Github or my entire understanding of Git/Github. This is just my attempt to study certain concepts of Git/Github, and to provide myself with notes for future references.

## What is Git?
A Version Control System (VCS) for tracking changes in a set of file. All we need to do is think about several people editting one word document and we can see where the need for a VCS arises from. 
A VCS will help with:
- Coordinate work between multiple developers across teams.
- Keep track of changes in files.
- Keep track of who made what changes and when.
- Revert to any point in the past.

## What is Github?
So Git and Github are not interchangable = they are both have different functionalities but they do work together very well. Git is the tool we use to control/track the changes made to a file , while Github is the hosting service to store Git repositories made using Git.

For example, say we have some file or some set of files, and we make changes and use Git to track these changes. When we use Git it creates a repository for this file/set of files. Now keep in mind, this repository is only available locally and cannot be accessed by anyone else, this is where Github comes in, it allows you to upload the repository to a more accessible location. 

## Centralized VCS (CVCS) vs Decentralized VCS (DCVS)
Git is a CVS and SVN is a DCVS. Essentially, CVCS requires network access at all times to use because you're using a central repository on a central server. DCVS on the other hand, you are working on a repository locally, and when you have network access, your local repository will be uploaded to a central server (Github).

## Three Three Architecture
When working Git keep in mind there are three trees rather than two trees. So rather than only having a working repository and the master repository where you only commit and checkout, there is a middle tree called the "staging index" which is used to store changes before commiting them to the master. The idea is that we can multiple changes to files at different times, store them on the staging index, and then commit them all at once. 

## Commit Messages
When commiting new messages it's important to consider what info you want to convey and how, especially if someone writes "git log --oneline". This will only show the first line of the commit message, so we can have a quick summary of all the commit messages, this is why you want to think ahead with writing a message. The first line should tell you enough about the commit so you remember what the change was.

Don't forget that when we commit, a message is always required. If we don't include "-m" at the end of the commit, an external editor will appear.

## Atomic Commits
Consider making all the changes in a commit related to each other, that why we easier describe the message and it makes sense. Also, it will be easier to make specific changes to the central repository, it only needs to commit to one type of change not all a bunch of them, this is useful, especially if they several other commits are not desirable.

## Git Ignore
If we wanted to ignore certain changes to our repository all we have to do is create a ".gitignore" file which have the names of the files we want to ignore. This files accepts regular expression as a mean of telling Git what type of files to ignore.

Going a step further, say we want to ignore a file that we tracked. Why would we want to do this? For example, we may just want to include the file initially in the repository but any changes after should not be tracked. Well all we do is include it in the ".gitignore" file of course but also remove it from the staging index by writing "git rm --cached 'filename'". Because it's a tracked file, Git will still want to track it despite being ignored, however we just tell Git to remove it from the staging area, it will never show up again.

## Tree Listing
Another neat thing about Git is that you can use it to not only show the revision comment or the changes in a file, but you can also see how the directory (also called a tree because it can branch off to other files or folders) looked in that revision. To do so, we use "Git ls-tree [Git Revision Here]". To go even further, we can look into one of the folders by writing "Git ls-tree [Git Revision Here] [Folder Name/].

## Resets in Git
We can actually roll back changes in Git using the "git reset" commands. You can specify what type of reset you want, there are 3 options, soft, mixed and hard. What it does is that it will take you to a previous Git revision, where you can recommit and remove any of the newer commits you made after the revision that you are now on. So keep in mind, commits in Git are not permenant, they can be removed using "Git Reset". 

## Merges
There are two types of merges, fast-forward merge and a true merge.

Fast-forward merge is when you merge a branch to the master and it's essentially an extension of master branch. The branch can easily be merged to the master as the master does not have its own commits. A true merge is the opposite of the fast-forward merge.

With true merges, you may have merge conflicts, this is where you have two branches, and both branches have different changes to one line. For the branches to merge, you will need to resolve the merge, there are tools to do resolve the merge, but you can do it manually. This just involves changing the code to the version you want. To reduce merge conflicts try to have the master merge with the branch often or have the branch merge with the master.

## Stashes
We can stash changes to commit later on or used on another branch. To do so, after we make a change, and we use the command "git stash save <file name>"
  
## Remote Repositories and Branches
To collaborate with others, we use a remote repository, a repository we store online on remote servers such as Github.

### Adding A Remote Repository onto your Git
To link your repository to a remote repository on git hub we use the command "git remote add origin <url>". The "origin" in the command is just the name, this can be anything. When you do this, your local repository is linked to this remote repository, but that's it. We haven't uploaded anything or cloned anything.
  
### Create a remote branch
To move one of the branches up into Github, we use the command "git push -u origin <branch name>". This will ask for a username and password. The "-u" is to make the branch a tracking branch, this is the branch that will try to stay as close as possible to branch to the one on the remote repository. It's also known as the upstream branch, it's the branch we are pushing changes to, it should be in alignment with the repository branch.
  
### To clone a remote repositroy
We need to click the "Clone" button in github, grab the url, and then open the folder you want to have the repository and then in git, write "git clone <url>".

### Track remote branches
Tracking the remote branches, means to have a branch in sync with the master as much as possible so it doesn't diverge too far (we're avoid having lots of merge conflicts).

### Fetching Branches
When you fetch from the remote server keep in mind that it does not merge anything with your current branches. It changes your tracking branch however.

## Bashrc & Bash_Profile
This file runs automatically anytime a Git Bash Windows opens. We can add code to this file by writing in the promopt "nano .bashrc" to run scripts and modify our Git Bash Window. 

The difference between these two can be found here: https://medium.com/@kingnand.90/what-is-the-difference-between-bash-profile-and-bashrc-d4c902ac7308. However the point is, these two files are run when the Git Bash Window is opened. To avoid worrying about which is being used, we have the bash_profile call out bashrc, see https://medium.com/@abhinavkorpal/bash-profile-vs-bashrc-c52534a787d3.

## Additional Important Commands in Git
Somse useful commands to remember in Git is:
- git help
  - This will show you all the git commands you can use and even detail them. Git commands appended to "git help" will provide you more details on the command. For example, if I wanted to know more about git log, I would write in the cmd window "git help log".
- git diff
  - Shows the changes made in the file that were commited before. Git compares the new file with the old file. 
  - Keep in mind that when you add a file to the staging index, the changes won't show in "git diff". You'll need to write "git diff  --staged". 
  - You can compare two different version by doing "git diff commit#...commit#2.... This also works with branches.
  - git diff by itself shows all the changes. If you're looking for a changes in a specfic file, then append the name of the file at the end.
- git show
  - This is followed by HEAD or the HASH code.
  - This shows your revision
  - In Git you can access ancestors of a revision by using ^. For example HEAD^ means "Show me what came before HEAD"
  - You can combine multiple '^' to find the parent, grandparent, great grandparent, etc. of a revision
- git log
  - Show all the revisions and their messages
  - If you look at the help page we can filter append a lot to this command to filter the git revisions
  
## Another Important Note
- Remember that files that start with "." do not show up in the folders, but it is there
  - These files can be used to track empty directories which are not tracked in Git. Add some "." file to tell git, "Hey, I'm not empty, track me!".
