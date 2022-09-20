---
title: CSC 217 Lab 01 - Project Creation
tags: [software engineering, software lifecycle, CS2, CSC216, Lab01]
description: Deployment
navigation: on
pagegroup: 01-lab
task: 9
---


{% include iconHeader.html type="deployment" %}
When you have deployed your software, you have released it to your customer.  For CSC216, that means your work is ready for evaluation by the teaching staff.  We will evaluate your work against the [Lab 01 rubric](#lab-rubric).  As you compare your submission against the rubric and make your final push to GitHub, you will complete these final tasks:

  * You have met the [requirements](01-lab-requirements) and [design](01-lab-design) for the [Lab 01 `PackScheduler`](../01-lab) project
  * You have a green ball on [your lab section's Jenkins](#lab-deadlines--jenkins-servers) (No test failures and no static analysis notifications)
  * All teaching staff JUnit tests pass with a green bar (0 errors).
  * You have run system level black box tests on your submission
  * There are no FindBugs notifications
  * There are no PMD notifications
  * There are no CheckStyle notifications
  * All code is commented with meaningful comments
  * [Javadoc webpages](#generate-javadoc) are generated with the latest comments
  * That you [meet all rubric items for the assignment](#lab-rubric)

Make sure that [all code and other required artifacts are pushed to GitHub](#push-to-github) by the [assignment deadline](#lab-deadlines--jenkins-servers).  [Check your Jenkins results](#check-jenkins) on [your lab's Jenkins server](#lab-deadlines--jenkins-servers)  **Lab assignments will not be accepted late!**

{% capture callout_content %}
To generate Javadoc, you need to [configure and run the Javadoc tool](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/gp1-javadoc#configure-and-run-javadoc-for-your-project), [fix Javadoc errors and warnings](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/gp1-javadoc#fix-javadoc-errors-and-warnings), and [check the generated Javadoc pages](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/gp1-javadoc#check-generated-javadoc-pages).  Make sure you push your changes to GitHub!
{% endcapture %}
{% include mention.html content=callout_content icon="dtTool" type="reminder" title="Reminder: Generating Javadoc" %}
## Generate Javadoc
{% include iconHeader.html type="dtTool" %}
Commenting your code is important! Comments describe what the code is supposed to do. At a minimum, you should comment your classes, fields, and methods. All methods should be Javadoc-ed, including methods that were automatically generated by Eclipse. When working with CSC 216 projects, you should delete any automatically generated non-Javadoc documentation and replace it with Javadoc appropriate for the overridden method.

Java provides the Javadoc tool to generate a set of web pages that display the comments for your code.


## Collaboration Check-in
Students working on teams must complete the [collaboration check-in]({{site.data.labs.collab-check}}) before the lab deadline.

## Lab Deadlines & Jenkins Servers
All labs are due 10 minutes before the start of the next lab.  Additionally, each lab section has their own dedicated lab Jenkins server.  The table below provides the deadline and server URL for each lab section for the current semester.

{% include lab_deadlines.md mon=site.data.labs.lab01.mon01 tues=site.data.labs.lab01.tues01 wed=site.data.labs.lab01.wed01 %}


{% capture callout_content %}
You will receive a certificate warning about a self-signed certificate when accessing the Jenkins servers for CSC216.  All of the certificates for CSC216 Jenkins servers were self signed personally by CSC IT.  Please accept the exception each time you visit a Jenkins server.
{% endcapture %}
{% include callout.html content=callout_content icon="ciTool" type="reminder" title="Reminder: Jenkins Certificate" %}



{% include rubric.md project="lab01" %} 

{% capture reminder-content %} 
GitHub Resources:

  * [Staging Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-staging)
  * [Committing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit)
  * [Pushing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-push)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Staging and Pushing to GitHub"%}
## Push to GitHub
Finalize your submission by pushing all of your code and other project artifacts to [GitHub](https://github.ncsu.edu)

  * Ensure all classes and methods are fully commented and your Javadoc pages are up to date.
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