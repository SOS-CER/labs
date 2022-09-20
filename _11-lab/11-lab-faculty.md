---
title: CSC 217 Lab 11 - Recursive Linked Lists
tags: [software engineering, software lifecycle, CS2, CSC 217, Lab11]
description: CSC 217 Lab 11 - Update and Test `Faculty`
navigation: on
pagegroup: 11-lab
---

# CSC 217 Lab 11 Update and Test `Faculty`
{% include iconHeader.html type="implementation,unitTest" %}
The `Faculty` class represents an individual faculty record - including the `FacultySchedule`.


## Add `FacultySchedule` State
Add a field of type `FacultySchedule` to `Faculty`.  

The `Faculty()` constructor should construct `FacultySchedule` and pass in the `Faculty` `id`.


## Add `Faculty.getSchedule()` Method
Add `Faculty.getSchedule()`, which returns the `FacultySchedule`.


## Add `Faculty.isOverloaded()` Method
Add `Faculty.isOverloaded()`, which returns true if the number of scheduled courses is greater than the `Faculty`'s `maxCourses`.


## Testing the New Functionality
Your `FacultyScheduleTest` tests will fail.  That's because you first have to update how `Course` and `CourseRecordIO` behave so that you can connect `Course`s and `Faculty` through `FacultySchedule`.


## Javadoc your Code
Javadoc the `Faculty` class, state, and methods.  For the overridden methods `equals()`, `hashCode()`, and `toString()`, remove the green comments and Javadoc them to describe how the methods work in `Faculty`.  Do NOT delete the `@Override` annotation.

Run [CheckStyle](../../gp1/gp1-static-analysis#checkstyle) to ensure that your Javadoc has all elements.

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



{% capture reminder-content %}
Check the following items on Jenkins for [your last build](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/jenkins/#build-summary-page) and use the results to [estimate your grade](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/jenkins/#grade-estimation-example):

  * [Test Results](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/jenkins/#test-results)
  * [Coverage Report](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/jenkins/#coverage-report)
  * [FindBugs Report](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/jenkins/#findbugs-report)
  * [CheckStyle Report](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/jenkins/#checkstyle-report)
  * [PMD Report](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/jenkins/#pmd-report)
{% endcapture %}
{% include mention.html content=reminder-content icon="ciTool" type="reminder" title="Reminder: Interpreting Jenkins" %}
## Check Jenkins
Check your project on Jenkins to ensure that you are making progress.
