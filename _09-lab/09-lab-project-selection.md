---
title: CSC 217 Lab 09 - Stacks and Queues
tags: [software engineering, software lifecycle, CS2, CSC 217, Lab09]
description: CSC 217 Lab 09 - Team Rotation 3 - Project Selection
navigation: on
pagegroup: 09-lab
---

# CSC 217 Lab 09: Team Rotation 3: Project Selection
Lab 09 is the last of three team rotations that will occur in CSC 217 labs this semester.  We rotate teams for several reasons, but the most important is so that you gain more experience working with a wider variety of students in CSC 217.  


## Select Project
Each team member will be coming into lab with their own project!  As a team, you'll need to select one project to move forward with. Discuss which project is the best starting point for moving forward. 


## Push Selected Project into GitHub
You have been assigned a new GitHub repository for the third team rotation: csc216-XXX-LLL-YY, where XXX is your lab section number and YY is your team number (LLL represents the third lab rotation).  

The owner of the selected team project will need to follow the process used in [Guided Project 2](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp2/gp2-repo.html) and [Guided Project 3](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp3/gp3-repo.html) for disconnecting a project from an existing repository and sharing it to a new repository.

Run all tests to ensure no regressions.


## Set Up Static Analysis Tools
Set up your project to automatically run FindBugs, PMD, and Checkstyle if the project isn't already set up for static analysis.


## Teammates Pull Selected Project from GitHub
Once the `PackScheduler` project is pushed to the new `LLL` repo, the other team members should clone the repo and import the `PackScheduler` project into their workspace.  If teammates don't have a laptop with them, they can complete this at a later time as they work outside of lab.

{% capture reminder-content %} 
GitHub Resources:

  * [Staging Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-staging)
  * [Committing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit)
  * [Pushing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-push)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Staging and Pushing to GitHub"%}
## Push to GitHub
Push your `PackScheduler` project to [GitHub](https://github.ncsu.edu)

  * Add the unstaged changes to the index.
  * Commit and push changes.  Remember to use a meaningful commit message describing how you have changed the code.  
  
Check that your job on Jenkins recognized the push to GitHub.
