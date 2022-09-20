---
title: CSC 217 Lab 03 - Collections
tags: [software engineering, software lifecycle, CS2, CSC 217, Lab03]
description: Testing CSC217Collections Library
navigation: on
pagegroup: 03-lab
---

When you work with a new library, it's a good idea to evaluate the library to ensure that it is an appropriate solution for  use in your system.  Additionally, by writing tests or interacting with the library on a small project, you can better understand how to integrate the library into your system.  Trying to immediately  integrate a library, especially into a large code base, is non-trivial and may lead to errors.

{% include iconHeader.html type="unitTest" %}


## Create a Package in the `test/` Folder
To test the CSC217Collections library, first create a new package, named `edu.ncsu.csc217.collections.list`, in the `test/` folder.  The package name matches the package name of the `SortedList` class that will be integrated into your project.  NOTE: We've been using `csc216` in the package names for our project thus far.  The CSC217Collections library has a different package name!  It's ok if you use `csc216` rather than `csc217` as the package name for your test.  If you use `csc216`, you'll need to import `SortedList` for testing.  If you use `csc217`, you will not need to import `SortedList` because it will be in the same package as your test.  We encourage the use of the `csc217` package to simplify imports and utilize common packages for source and test files.


## Create `SortedListTest`
Create a new JUnit test class named `SortedListTest`.  You will NOT be able to create the JUnit class by clicking on the `SortedList` file.  Instead, right click on the new `edu.ncsu.csc217.collections.list` package and select **New > JUnit Test Case**.


## Copy in Skeleton `SortedListTest`
[Copy the skeleton `SortedListTest` class](files/SortedListTest.java) into your project's `SortedListTest` class.  

The skeleton `SortedListTest` provides `TODO` markers that describe the types of tests that you should write for each of `SortedList`'s methods.


## Testing Lists
Testing lists involves thinking about 4 scenarios appropriate for the given test: 1) empty list, 2) working at the front of the list, 3) working in the middle of the list, and 4) working at the end of the list.  The table below provides some suggested tests for major list functionality:

|Method|Empty List|Front of List|Middle of List|End of List|
|:-----|--------------------------|--------------------------|--------------------------|--------------------------|
|`add()`|Adding first element to the list|Adding to the front of the list|Adding to the middle of the list|Adding to the end of the list|
|`remove()`|Removing from an empty list & removing the last element from the list|Removing  the first element|Removing a middle element|Removing the last element|
|`get()`|Getting from an empty list|Getting from the front of the list|Getting from the middle of the list|Getting from the back of the list|

The `TODO` markers identify the scenarios that you want to test.  When testing, it is not enough to verify that the size is correct after adding and removing.  You should also verify that each element is in the correct location of the list using the `get()` method.

The CSC217Collections library has no intentionally seeded bugs.  And while the library is well tested (your test class and the TODO are based on the teaching staff library tests) there may be unanticipated bugs in the library.  If you find one, please let your PTF or instructor know so it can be fixed!


## Comment `SortedListTest`
The provided skeleton is uncommented.  One way to better understand the tests that you will be writing is to comment the class and each of the test methods with details about the test.  Comment `SortedListTest` with meaningful comments so that there are no CheckStyle notifications.


## Collaboration
If you're in an synchronous lab, switch drivers after completing each test method.  That way each person gains experience writing unit tests for a list.  This will be the first of many times that you're expected to write tests for lists.


## Test `SortedList()`
The first thing that you should test is that the `SortedList` object is constructed correctly.  A new constructed `SortedList` object should be empty. Write a test that confirms  the list object is constructed correctly by checking that the `size()` is zero and the list `isEmpty()`.

The `SortedList()` test should also evaluate that the list will grow correctly.  As stated in the [Javadoc](javadoc/edu/ncsu/csc217/collections/list/SortedList.html), the initial capacity is 10.  Add at least 11 elements to ensure that the list grows without error.

Note that the `SortedList` object in the test class is parameterized for `String`s and not `Student`s.  You cannot yet test with `Student` objects because `Student` does not yet implement the `Comparable` interface.  Additionally, testing with another type besides the one intended for use in the project ensures that the generic implementation works correctly.


## Test `add(E)`
Now that you are confident that the list is constructed correctly, you should test that elements are added to the list correctly.  While you used the `add()` method in testing that the list grows correctly in the constructor, the test for `add()` is going to focus on the specifics of the `add()` method.   If you aren’t confident in adding elements, the rest of your tests are invalid!

There is an example test of adding the first element to the list.  [Read the Javadoc for the `add()` method](javadoc/edu/ncsu/csc217/collections/list/SortedList.html#add-E-) and build on the provided test to test the following scenarios:

  * Add an element to the front (such as a `String` that comes before "banana")
  * Add an element to the end
  * Add an element to the middle
  * Add a null element
  * Add a duplicate element
  
When testing `add()`, you shouldn't check only the size.  You should also check that each element is in the correct order.
  

## Test `get(int)`
The main functionality of the `get()` method is tested in the other test methods.  The `testGet()` method focuses on testing the edge and error cases for `get()`.  

[Read the Javadoc for the `get()` method](javadoc/edu/ncsu/csc217/collections/list/SortedList.html#get-int-) and test the following scenarios:

  * Getting an element from an empty list
  * Adding some elements to the list, and getting an element at an index less than 0
  * Getting an element at index `size()`
  
 
## Test `remove(int)`
[Read the Javadoc for `remove()`](javadoc/edu/ncsu/csc217/collections/list/SortedList.html#remove-int-) and test the following scenarios:

  * Removing an element from an empty list
  * Adding at least four elements and removing an element at an index less than 0
  * Removing an element at index `size()`
  * Removing a middle element
  * Removing the last element
  * Removing the first element
  * Removing the last element
  

## Test `indexOf(E)`
[Read the Javadoc for `indexOf()`](javadoc/edu/ncsu/csc217/collections/list/SortedList.html#indexOf-E-) and test the following scenarios:

  * Getting the index of an element in an empty list
  * Adding some elements and getting the index of elements in various positions in the list
  * Getting the index of elements not in the list
  * Getting the index of a null element
  

## Test `clear()`
[Read the Javadoc for `clear()`](javadoc/edu/ncsu/csc217/collections/list/SortedList.html#clear--)  and test the following scenarios:

  * Adding at least one element to the list
  * Clearing the list
  * Checking that the list is empty


## Test `isEmpty()`
[Read the Javadoc for `isEmpty()`](javadoc/edu/ncsu/csc217/collections/list/SortedList.html#isEmpty--)  and test the following scenarios:

  * Checking a new list is empty
  * Adding an element
  * Checking that the list is now not empty
  

## Test `contains()`
[Read the Javadoc for `contains()`](javadoc/edu/ncsu/csc217/collections/list/SortedList.html#contains-E-)  and test the following scenarios:

  * Checking if an empty list contains an element
  * Adding elements and checking if the list contains an element in the list
  * Checking if a list contains an element not in the list 
  

{% capture callout_content %}
[See the instructions in Lab02 about testing `equals()` and `hashCode()`.](../02-lab/02-lab-student#testing-students-hashcode-and-equals)  Use a similar strategy here.
{% endcapture %}
{% include mention.html content=callout_content icon="plTool" type="reminder" title="Reminder: Testing `equals()` and `hashCode()` Methods" %}
## Test `equals()` and `hashCode()
Test the `equals()` and `hashCode()` methods.



  
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
Make sure that you have a job and it's pulling from GitHub.

Your project will have a red ball.  That is because you have not yet completed some of the refactorings that the teaching staff tests will expect.  Therefore, the teaching staff tests are still unable to compile against your code. 
