---
title: CSC 217 Lab 05 - Inspection & Debugging
tags: [software engineering, software lifecycle, CS2, CSC 217, Lab05]
description: CSC 217 Lab 05 - Testing & Debugging
navigation: on
pagegroup: 05-lab 
---

# CSC 217 Lab 05: Testing & Debugging
{% include iconHeader.html type="unitTest,systemTest" %}
As with any software development project, you must test your code to know if it meets the [requirements](05-lab-requirements) and [design](05-lab-design).  You should have unit tested your new code as you integrated and debugged `RegistrationManager`.  Now you will ensure sufficient coverage and system test `PackScheduler`.


## `PackScheduler` Coverage
Ensure that all non-UI classes have at least 80% statement coverage.  Add any needed tests to cover at least 80% of the statements.

 
## `PackSchedulerGUI`
The teaching staff has provided three classes that comprise the GUI for `PackScheduler`.  Create classes `PackSchedulerGUI`, `CourseCatalogPanel`, and `StudentDirectoryPanel` in the `edu.ncsu.csc216.pack_scheduler.ui` package and copy in the provided code.  Note that there are updates to `StudentDirectoryPanel`, so you should use the provided code.

  * [`PackSchedulerGUI` Code](files/PackSchedulerGUI.java)
  * [`CourseCatalogPanel` Code](files/CourseCatalogPanel.java)
  * [`StudentDirectoryPanel` Code](files/StudentDirectoryPanel.java)
  

## System Testing and Debugging
[Download a copy of the system tests for `PackScheduler`](https://docs.google.com/a/ncsu.edu/document/d/1k32Wv7umWr8qeO6PGbQP8hCzOeWPpCyp4rnGT0Xkuy4/edit?usp=sharing).  Save the system test plan file in the `project_docs` folder.

Do the following:

  * Run the tests on the `PackScheduler` project.  If the test fails, debug your system until it passes.
  * Report the actual results of execution after debugging your system.
  
The following files are needed for testing (some you already have):

  * [student_records.txt](files/student_records.txt)
  * [course_records.txt](files/course_records.txt)
  * [expected_t19_student_directory.txt](files/expected_t19_student_directory.txt)
  * [expected_t39_course_catalog.txt](files/expected_t39_course_catalog.txt)

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
Check Jenkins and make sure that you have a green check and are passing your tests AND the teaching staff tests (both unit and system)!

