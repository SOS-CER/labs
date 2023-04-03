---
title: CSC 217 Lab 10 - Iterators
tags: [software engineering, software lifecycle, CS2, CSC 217, Lab10]
description: Testing
navigation: on
pagegroup: 10-lab
---


As with any software development project, you must test your code to know if it meets the [requirements](10-lab-requirements) and [design](10-lab-design).  You should have unit tested your new code as you added functionality functionality.  Now you will ensure sufficient coverage and system test `PackScheduler`.

{% include iconHeader.html type="unitTest,systemTest" %}


## `PackScheduler` Coverage
Ensure that all non-UI classes have at least 80% statement coverage.  Add any needed tests to cover at least 80% of the statements.

The introduction of the new faculty functionality shouldn't lead to the regression of any existing tests.  If so, update the test to reflect the new requirements. 


## `PackSchedulerGUI`
The teaching staff has provided five classes that comprise the GUI for `PackScheduler`.  Create classes `PackSchedulerGUI`, `CourseCatalogPanel`,  `StudentDirectoryPanel`, `FacultyDirectoryPanel`, and `StudentRegistrationPanel` in the `edu.ncsu.csc216.pack_scheduler.ui` package and copy in the provided code.  The `FacultyDirectoryPanel` class is new and `PackSchedulerGUI` has updates.

  * [`PackSchedulerGUI` Code](files/PackSchedulerGUI.java)
  * [`CourseCatalogPanel` Code](files/CourseCatalogPanel.java)
  * [`StudentDirectoryPanel` Code](files/StudentDirectoryPanel.java)
  * [`FacultyDirectoryPanel` Code](files/FacultyDirectoryPanel.java)
  * [`StudentRegistrationPanel` Code](files/StudentRegistrationPanel.java)
  

## System Testing and Debugging
System test the new Faculty functionality to ensure it works correctly.  

The following files are needed for testing.  Note that there are now four new files for testing faculty functionality!

  * [student_records.txt](files/student_records.txt)
  * [course_records.txt](files/course_records.txt)
  * [expected_course_catalog.txt](files/expected_course_catalog.txt)
  * [expected_course_records.txt](files/expected_course_records.txt)
  * [starter_course_records.txt](files/starter_course_records.txt)
  * [t19_student_directory.txt](files/t19_student_directory.txt)
  * [t39_course_catalog.txt](files/t39_course_catalog.txt)
  * [faculty_records.txt](files/faculty_records.txt)
  * [expected_faculty_records.txt](files/expected_faculty_records.txt)
  * [invalid_faculty_records.txt](files/invalid_faculty_records.txt)
  * [expected_full_faculty_records.txt](files/expected_full_faculty_records.txt)

{% capture reminder-content %} 
GitHub Resources:

  * [Staging Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-staging)
  * [Committing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit)
  * [Pushing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-push)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Staging and Pushing to GitHub"%}
## Push to GitHub
Push your `PackScheduler` project to [GitHub](https://github.ncsu.edu).

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
Ensure that your Jenkins job is reflecting the results that you expect for the level of completion of your lab assignment.
