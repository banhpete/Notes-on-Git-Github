# Understand-Git-GitHub
Just some notes on Git/GitHub based on https://www.ajonit.com/git/what-is-git/

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

## Important Commands in Git
Somse useful commands to remember in Git is:
- git help
  - This will show you all the git commands you can use and even detail them. Git commands appended to "git help" will provide you more details on the command. For example, if I wanted to know more about git log, I would write in the cmd window "git help log".
- git diff
  - Shows the changes made in the file that were commited before. Git compares the new file with the old file. 
  - Keep in mind that when you add a file to the staging index, the changes won't show in "git diff". You'll need to write "git diff  --staged". 
  - You can compare two different version by doing "git diff commit#...commit#2....
  - git diff by itself shows all the changes. If you're looking for a changes in a specfic file, then append the name of the file at the end.
- git show
  - This is followed by HEAD or the HASH code.
  - This shows your revision
  - In Git you can access ancestors of a revision by using ^. For example HEAD^ means "Show me what came before HEAD"
  - You can combine multiple '^' to find the parent, grandparent, great grandparent, etc. of a revision
  
## Another Important Note
- Remember that files that start with "." do not show up in the folders, but it is there
  - These files can be used to track empty directories which are not tracked in Git. Add some "." file to tell git, "Hey, I'm not empty, track me!".
