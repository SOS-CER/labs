---
title: CSC 217 Credit by Exam
tags: [software engineering, software lifecycle, CS2, CSC 217]
description: CSC 217 CBE - Overview
navigation: on
---

# CSC 217 Software Development Fundamentals Lab - Credit-by-Exam
The CSC 217 Software Development Fundamentals Lab Credit-by-Exam (CBE) process requires the implementation and testing of several utility classes to demonstrate skills related to the learning outcomes listed below.  A grade of 70 or higher is required on the CBE to receive credit for CSC 217.  Additionally, you must earn at least 10 points on each of the sub-areas to receive credit, assuming a total of 70 or higher is earned.

## Course Description
{{ site.data.courseInfo.description }}

## Learning Outcomes
Upon successful completion of this course, a student will be able to...

{% for outcome in site.data.courseInfo.outcomes %}
  1. {{outcome}}
{% endfor %}
  

## CSC 217 CBE Overview
{% include iconHeader.html type="task" %}
The CSC 216 CBE will be completed in the following steps:

{% include tableOfContents.html pagegroup="cbe" %}


## Timeline
You will have two weeks to complete the CSC 217 CBE activities.  The course coordinator will provide the specific deadline for your CBE.

## Resources
You will be provided the following:

  - [GitHub repository](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/): You must use the provided GitHub repository for completing your work. All code must be pushed to the `main` branch by the given deadline for evaluation.
  - [Jenkins job](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/jenkins/): Most of your work will be automatically assessed via Jenkins.  You can use the feedback to improve your work.

{% include cbe-rubric.md project="cbe" %} 
