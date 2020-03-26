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

