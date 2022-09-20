---
title: CSC 217 Lab 08 - LinkedAbstractList
tags: [software engineering, software lifecycle, CS2, CSC 217, Lab08]
description: CSC 217 Lab 08 - Update `Schedule` and `Student`
navigation: on
pagegroup: 08-lab
---
# CSC 217 Lab 08 Update `Schedule` and `Student`
{% include iconHeader.html type="implementation,unitTest" %}
`Schedule` and `Student` need a few additional methods to support functionality at in the `RegistrationManager` - the ability to check if the `Course` can be added to the `Student`'s `Schedule`.


## Update `Schedule`
`Schedule` requires two new methods: `getScheduleCredits()` and `canAdd()`.  Write tests and then implement the methods as they are described below:

  * `getScheduleCredits()` is a cumulative sum that returns the total credits in the `Schedule`.
  * `canAdd()` returns true if the `Course` can be added to the schedule.  If the `Course` is null, if the `Course` is already in the schedule, or if there is a conflict, `canAdd()` will return false.

The `Schedule.getScheduledCourses()` should be updated to include a 5th column.  Since `Course.getShortDisplayArray()` now has 5 elements, the `scheduleArray` in `Schedule.getScheduledCourses()` needs the 5th column too.


## Update `Student` Class
`Schedule` doesn't know anything about the max number of credits that can go in a `Student`'s `Schedule`, but `Student` does.  Therefore, `Student` needs a `canAdd()` method.  Write tests and then implement the `canAdd()` method.

  * `canAdd()` returns true if the `Course` can be added to the `Student`'s `Schedule`.  If the `Course` is null, if the `Course` is already in the schedule, if there is a conflict, or if the `Student` has no more room in their schedule for the course (i.e., adding the `Course` would exceed their max allowed credits), `canAdd()` will return false.  Note that `Student.canAdd()` can call `Schedule.canAdd()`, which handles the first three checks already.

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


