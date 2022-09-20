---
title: CSC 217 Credit by Exam
tags: [software engineering, software lifecycle, CS2, CSC 217]
description: CSC 217 CBE - Setup
navigation: on
pagegroup: cbe
---

# CSC 217 CBE - Setup
You will need to complete the following tasks for the CSC 217 CBE.

## Development Environment
Follow the instructions for the [CSC 216/217 Development Environment Set-up](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/eclipse/eclipse-install.html) to ensure that you have all the tools necessary for completing the CSC 217 CBE.

## GitHub
Clone your provided GitHub repository.  See the [Git Guide](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-clone).  for info on cloning a GitHub repository in Eclipse.
## Project
Create an Eclipse project named `CSC217CBE`.  The project name is case sensitive; all letters should be uppercase.

Complete the following steps to ensure your project is configured correctly:

  - Create a new source folder named `test`.  Right click on the project and select **New > Source Folder**. 
  - Add **JUnit 4** to the build path.  Right click on the project and select **Properties > Java Build Path > Libraries tab**.  Click on **Classpath**, click **Add Library**, select **JUnit**.  In the drop down make sure you select **JUnit 4**.  Click **Finish**.
  - Set up static analysis tools to run on the project.  Right click on the project and select **Properties**.  Do the following for each tool:
     - Checkstyle: Select **Checkstyle active for this project**.  Make sure the CSC216/217 rule set is selected.
	 - PMD: Select **Enable PMD**. Make sure there are 
	 - SpotBugs: Select **Enable Project Specific Settings** and **Run automatically**.  Make sure that the slider is set to **9 (Scary)**.

## Create Package & Classes
Create the first package, source class, and test class.  This will create the appropriate directory structure and support pushing everything to GitHub with minimal errors.

  - Create package `edu.ncsu.csc217.cbe.fsm` in both the `src/` and `test/` folders.
  - Create a Java class `CourseNameValidator` in the `edu.ncsu.csc217.cbe.fsm` package of the `src/` folder.
  - Create a JUnit class `CourseNameValidatorTest` in the `edu.ncsu.csc217.cbe.fsm` package of the `test folder.

## Commit/Push to GitHub
Share your project with your CBE GitHub repository.  Commit/push the changes to the remote.  Browse to your provided GitHub repository on github.ncsu.edu and ensure that your repo contains the `CSC217CBE` folder in the `main` branch of your repo.  If the repo is not set up properly, your project will not build on Jenkins.  

You can also check that the Jenkins build is pulling from your repo and failing due to compiler errors by going to the provided Jenkins URL for your CBE.  At this point,  you will have a red ball, but you can check the build's console output to see if there are compiler errors.  If there are, your project structure is correct for building. If you see anything about a missing `CSC217CBE` directory, the project structure in GitHub is likely incorrect and you should email for help.