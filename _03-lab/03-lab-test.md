---
title: CSC 217 Lab 03 - Collections
tags: [software engineering, software lifecycle, CS2, CSC 217, Lab03]
description: System Testing
navigation: on
pagegroup: 03-lab
---

As with any software development project, you must test your code to know if it meets the [requirements](03-lab-requirements) and [design](03-lab-design).  You have now refactored and tested `Student`, `StudentRecordIO`, and `StudentDirectory` and achieved at least 80% statement coverage (hopefully more).  Now, you need to incorporate the GUI and complete system level testing to ensure that the full program meets the requirements.

{% include iconHeader.html type="systemTest" %}

## Update System Tests
In Lab 02, you wrote at least 15 system tests for the `StudentDirectory` portion of `PackScheduler`.  Each test considered a different equivalence class or boundary value (which should be labeled under the Test ID).  Remember to use repeatable and specific values.  

Update these tests to reflect the new sorted order functionality.  Then execute them and record the actual results.

Any new input or expected output files should be created and placed in your `test-files/` directory so the teaching staff can run your tests. 

Report actual results of execution.

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
  
Since we can't automate system tests, you won't need to check Jenkins.  But you should make sure that your System Test Plan was submitted!

