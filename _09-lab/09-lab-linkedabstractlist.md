---
title: CSC 217 Lab 09 - Stacks and Queues
tags: [software engineering, software lifecycle, CS2, CSC 217, Lab09]
description: CSC 217 Lab 09 - `LinkedAbstractList` Optimization
navigation: on
pagegroup: 09-lab
---

# CSC 217 Lab 09 `LinkedAbstractList` Optimization
{% include iconHeader.html type="implementation,unitTest" %}
Both the `ArrayQueue` and `LinkedQueue` implementations have an O(n) runtime for either `enqueue()` or `dequeue()` depending on what end of the list your considered the front.  There's nothing you can do to improve the efficiency of `ArrayQueue` - a right or left shift has to happen to maintain the `ArrayList`.  But you can improve the efficiency of your `LinkedQueue` by adding an optimization to `LinkedAbstractList`.  


## Add `back` Field
To improve the `enqueue()` operation, you can add an additional field to your `LinkedAbstractList`, `back`.  The `back` field will point to the last node in the list.  That means you can create special, efficient cases for adding at the end of the list.  However, *removing* from `LinkedAbstractList` will still require traversal since the list is singly linked, but since you are using the `back` reference for improving efficiency for queues, removing from the end of the list is not a concern since (with queues), you  remove only from the beginning of the list.

Add the `back` field.


## Update `add(int idx, E element)`
Update `add()` so that `back` always references to the last element. There's a special case for adding the first element to the list.

Additionally, add the special constant-time case for adding to the back of the list to avoid the traversal!


## Update `remove(int idx)`
Update `remove()` so that `back` always references the last element. 


## Update `size()`
If size is not maintained as a field, add it. Returning the `size` field in the `size()` method is constant time.  Additionally, it may be used in `isEmpty()` so that `isEmpty()` also runs in constant time.  

Make sure you increment/decrement size from within the `add()` and `remove()` methods.


## Test!
Run your unit tests.  Ensure there are no regressions in functionality by adding the new field.

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
