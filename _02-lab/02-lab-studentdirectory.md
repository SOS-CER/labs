---
title: CSC 217 Lab 02 - Software Engineering Best Practices
tags: [software engineering, software lifecycle, CS2, CSC 217, Lab02]
description: Unit Test `StudentDirectory`
navigation: on
pagegroup: 02-lab
---

You have been provided `StudentDirectory` for Lab 02.  Additionally, you were provided **some** unit tests for `StudentDirectory`, but not enough to meet the 80% statement coverage threshold for `StudentDirectory`. You will write additional unit tests to fully cover `StudentDirectory`.  

{% include iconHeader.html type="unitTest" %}

`StudentDirectory` represents a list of `Student` records in our system.  The method descriptions below describe what each method should do.  You will write unit/integration tests to ensure that the methods do these things correctly.  If you find any bugs in `StudentDirectory` (it is possible, but hopefully unlikely), please let the teaching staff know.  That way we can share with the rest of the class so everyone moves forward with bug free code!  


{% capture callout_content %}
There are several resources provided for writing tests, including sample test code:

  * [Testing Packet](https://pages.github.ncsu.edu/engr-csc116-staff/CSC116-Materials/testing/version/6.0.0/)
  * [Dr. Heckman's Testing Lecture Notes](https://pages.github.ncsu.edu/engr-csc216/Heckman/slides/02_TestingDebugging.pdf)
  * [Seasons Test Example](https://pages.github.ncsu.edu/engr-csc216/Heckman/resources/02_Testing.zip)
  * [Dr. Heckman's Coverage and Static Analysis Lecture Notes](https://pages.github.ncsu.edu/engr-csc216/Heckman/slides/03_Coverage_StaticAnalysis.pdf)
  * [Guided Project 1 CourseTest.java](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/files/CourseTest.java)
  
Note that the tests for `StudentDirectory` are similar to the [tests for `WolfScheduler`](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/files/WolfSchedulerTset.java) in Guided Project 1.  You may use those tests as examples and reference for Lab 2!
{% endcapture %}
{% include mention.html content=callout_content icon="ttTool" type="reminder" title="Reminder: Resources on Writing Tests" %}
## Testing Strategies
There are no descriptions of what you should test here.  By this point you should have enough practice with testing to start thinking of your own tests for each of these methods!

Your goal to to achieve at least 80% statement coverage by writing high quality tests that exercise most of the paths in your `StudentDirectory` class.  There is 1 point of extra credit for exceeding 90% statement coverage, an additional point of extra credit for obtaining at least 96% statement coverage, and a third point of extra credit for achieving 100% condition coverage!

Make sure you are frequently running your tests!  If you find a bug in your solution, fix it!





## `StudentDirectory` State
`StudentDirectory` has an `ArrayList` of `Students` that represent the student directory for the university.  

There is also a constant value for the hash algorithm used to hash the passwords when adding a new `Student`.  We're using [**SHA-256**](https://en.wikipedia.org/wiki/SHA-2).  By providing the hash algorithm as a constant, you reduce the chance of throwing a `NoSuchAlgorithmException` due to a mistype.


## `StudentDirectory` Constructor
The `StudentDirectory` constructor initializes the `studentDirectory` field by calling the `newStudentDirectory()` method. 


## `newStudentDirectory()`
This method supports the functionality for a new student directory described in [[UC2]](02-lab-requirements#uc2).  `studentDirectory` is updated to refer to a new `ArrayList` of `Student`s (which is then empty).

{% capture callout_content %}
You will need to use similar strategies for handling hashed passwords that you used when testing `StudentRecordIO`.
{% endcapture %}
{% include mention.html content=callout_content icon="plTool" type="reminder" title="Reminder: Hashed Passwords when Testing" %}
## `loadStudentsFromFile()`
This method supports the functionality for loading a list of student records from a file as described in [[UC3]](03-lab-requirements#uc3). If the call to `StudentRecordIO.readStudentRecords()` throws a `FileNotFoundException`, a new `IllegalArgumentException` is thrown by `StudentDirectory.loadStudentsFromFile()` to the GUI or test class.  The provided message may be used in a dialog as described in [[UC3 - Invalid File]](02-lab-requirements#uc3).




## `addStudent()`
This method supports the functionality for adding a `Student` to the list of students as described in [[UC5]](02-lab-requirements#uc5).  The method also covers several Alternative Flows.  The first grouping of error messages come from `IllegalArgumentException`s thrown during construction of `Student` or when checking the `password` and `repeatPassword` parameters.  


An error related to "Cannot hash password" should hopefully never happen, but an exception with a error message is provided in case it ever does.  You will NOT be expected to write a test to cover this exception. If this is the only uncovered line in `StudentDirectory` you will receive full extra credit.

By returning `false`, the method will trigger the error message associated with [[UC5 - Non-unique ID]](02-lab-requirements#uc5), which is part of the GUI implementation.


## `removeStudent()`
This method supports the functionality for removing a `Student` from the list of students as described in [[UC6]](02-lab-requirements#uc6).


## `getStudentDirectory()`
This method returns a 2D array, where each row is a `Student` and the columns are for the `firstName`, `lastName`, and `id`.  The 2D array is required so that the information can be displayed in the table used in the GUI.

{% capture callout_content %}
You will need to use similar strategies for handling hashed passwords that you used when testing `StudentRecordIO`.
{% endcapture %}
{% include mention.html content=callout_content icon="plTool" type="reminder" title="Reminder: Hashed Passwords when Testing" %}
## `saveStudentDirectory()`
This method saves the `studentDirectory` to the given file.  If `StudentRecordIO.writeStudentRecords()` throws an `IOException`, a new `IllegalArgumentException` is thrown.  The provided message may be used in a dialog as described in [[UC4]](02-lab-requirements#uc4).  Use the same strategy to cause an `IOException` that you used when testing `StudentRecordIO.writeStudentRecords()` for full coverage.




## Run Your Tests
Run your tests instrumented for coverage.  Make sure that your tests execute at least 80% of the statements in `StudentDirectory`.  Remember there is extra credit for more coverage!
    

## Javadoc your Code
Make sure that you Javadoc the `StudentDirectoryTest` class and methods. 

Run [CheckStyle](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/gp1-static-analysis#checkstyle) to ensure that your Javadoc has all elements.

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
At this point, your project should build on Jenkins, hopefully with a green check!  If not, work through Jenkins's feedback to fix any errors with the integration of your code with the provided code.  All tests should be passing before you walk through the GUI.
