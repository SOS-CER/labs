---
title: CSC 217 Lab 04 - Design
tags: [software engineering, software lifecycle, CS2, CSC 217, Lab04]
description: Testing
navigation: on
pagegroup: 04-lab
---

As with any software development project, you must test your code to know if it meets the [requirements](04-lab-requirements) and [design](04-lab-design).  You should have been running your tests cases as you integrated the two systems together.  Now, you will focus on unit testing for coverage.

{% include iconHeader.html type="unitTest,systemTest" %}


## `PackScheduler` Coverage
Ensure that all non-UI classes have at least 80% statement coverage.  Add any needed high quality tests to cover at least 80% of the statements in non-UI classes.


## System Testing
For the moment, you will forgo system testing.  Since there were no changes to `Student`, `StudentRecordIO`, and `StudentDirectory`, we do expect that your `StudentDirectoryPanel` tests will continue to pass (and you're welcome to run them to make sure they still do).  However, the GUI for the `Course` side of the project has not yet been provided so we will not be evaluating your application at a system test level for Lab 04.

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
Check that Lab 4 is building and that your tests and the teaching staff tests are all passing.  Remember, 80% statement coverage is needed for all non-UI classes for the teaching staff tests to run.

