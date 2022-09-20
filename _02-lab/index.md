---
title: CSC 217 Lab 02
tags: [software engineering, software lifecycle, CS2, CSC 217, Lab02]
description: Software Engineering Best Practices
---

# CSC 217 Lab 02: Software Engineering Best Practices
For Lab 02, you will test the `PackScheduler` project you developed in Lab 01.  For Lab 01, your project was evaluated against the teaching staff test suite.  Now you will develop your own test suite to demonstrate that your program meets the [`PackScheduler` requirements](02-lab-requirements).


{% capture callout_content %}
  * Write unit tests for `Student`, `StudentRecordIO`, and `StudentDirectory`
  * Achieve at least 80% statement coverage when executing your tests against   `Student`, `StudentRecordIO`, and `StudentDirectory`
  * Use code coverage tools to identify other paths to test
  * Use static analysis tools to identify potential problems
  * Write and run black box tests
  * Find an fix any bugs detected during testing
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}


{% if site.data.labs.lab02open %}
## Lab Overview
{% include iconHeader.html type="task" %}
For students in async lab sections (Sections 231 and 601), watch the [Lab 02 Overview Video](https://ncsu.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=8e75cdc1-5364-4ce2-b447-ae2d00072ecc).


The lab will be completed in the following steps:

{% include tableOfContents.html pagegroup="02-lab" %}

{% endif %}

 
## Lab Deadlines & Jenkins Servers
{% include iconHeader.html type="overview" %}
All labs are due 10 minutes before the start of the next lab.  Additionally, each lab section has their own dedicated lab Jenkins server.  The table below provides the deadline and server URL for each lab section for the current semester.

<!--
{% capture callout_content %}
You will receive a certificate warning about a self-signed certificate when accessing the Jenkins servers for CSC 217.  All of the certificates for CSC 217 Jenkins servers were self signed personally by Dr. Heckman.  Please accept the exception each time you visit a Jenkins server.

Also note that permissions to the Jenkins server are at the job level.  If you have no permissions to any job, you will be unable to sign into the Jenkins server.  Once jobs are created,  you will be able to sign in.
{% endcapture %}
{% include callout.html content=callout_content icon="ciTool" type="reminder" title="Reminder: Jenkins Certificate Warnings" %}
-->
 
{% include lab_deadlines.md mon=site.data.labs.lab02.mon02 tues=site.data.labs.lab02.tues02 wed=site.data.labs.lab02.wed02 %}

 

{% include rubric.md project="lab02" extra-credit="true" %} 

