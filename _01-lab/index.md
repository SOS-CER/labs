---
title: CSC 217 Lab 01
tags: [software engineering, software lifecycle, CS2, CSC216, Lab01]
description: Project Creation
pagegroup: 01-lab
---


For Lab 01, you will start work on the `PackScheduler` project that will be developed throughout the semester as part of the lab activities.


{% capture callout_content %}
  <!--* Practice working on a pair or small team to understand the benefits-->
  <!--* Learn about the version control system GitHub-->
  * Work with an Eclipse project, packages, and classes
  * Implement a plain old java object class
  * Implement file I/O
  * Use composition
  * Run unit tests
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}
  


## Pre-lab Activity:
{% include iconHeader.html type="ideTool" %}
Go through the [Eclipse Install Tutorial](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/eclipse/eclipse-install.html).  Note down any problems that you run into.  Ask questions about install issues on Piazza!



## Lab Overview
{% if site.data.labs.lab01open %}
For students in async lab sections (Section 651), watch the [Lab 01 Overview Video](https://ncsu.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=2b6fa96a-8e80-4ffb-bf4b-ad8b002205f8).  Note the deadlines for YOUR lab are in the lab writeup!

{% include iconHeader.html type="task" %}
The lab will be completed in the following steps:

{% include tableOfContents.html pagegroup="01-lab" %}

{% else %}
This lab is not yet open. 

{% endif %}


## Lab Deadlines & Jenkins Servers
{% include iconHeader.html type="overview" %}
All labs are due 10 minutes before the start of the next lab.  Additionally, each lab section has their own dedicated lab Jenkins server.  The table below provides the deadline and server URL for each lab section for the current semester.


{% include lab_deadlines.md mon=site.data.labs.lab01.mon01 tues=site.data.labs.lab01.tues01 wed=site.data.labs.lab01.wed01 %}


{% include rubric.md project="lab01" %}  
