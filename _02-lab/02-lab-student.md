---
title: CSC 217 Lab 02 - Software Engineering Best Practices
tags: [software engineering, software lifecycle, CS2, CSC 217, Lab02]
description: Unit Test `Student`
navigation: on
pagegroup: 02-lab
---

The `Student` class represents an individual student record.  The `Student` class is a "plain old java object" (POJO) consisting mostly of getters and setters.  The setters do have some complexity and you need to test `Student` to ensure that your setters work correctly and that a `Student` object is constructed correctly. 

{% include iconHeader.html type="unitTest" %}


## Create a `StudentTest` Class
To create the `StudentTest` class, do the following:

  * Right click on `Student` and select **New > JUnit Test Case**. 
  * Change the **Source folder** to `/PackScheduler/test`.  Click **Next**.
  * Select the `Student` constructors, all public setters, `hashCode()`, `equals()`, and `toString()`.  Click **Finish**.
  * A new class `StudentTest` will be created in the `edu.ncsu.csc216.pack_scheduler.user` package in the `test/` source folder. `StudentTest` will contain empty test methods for the `Student` constructors, all public setters, `hashCode()`, `equals()`, and `toString()` methods.  Note that you will need to call the getters to see that the internal state of `Student` has changed correctly.  You'll get coverage of the getters through other test cases.
  
If the `StudentTest` file isn't in the right package or source folder, move it to the appropriate location.  If it's not in the right place, your tests may not be executed on Jenkins!


{% capture callout_content %}
There are several resources provided for writing tests, including sample test code:

  * [Testing Packet](https://pages.github.ncsu.edu/engr-csc116-staff/CSC116-Materials/testing/version/6.0.0/)
  * [Dr. Heckman's Testing Lecture Notes](https://pages.github.ncsu.edu/engr-csc216/Heckman/slides/02_TestingDebugging.pdf)
  * [Seasons Test Example](https://pages.github.ncsu.edu/engr-csc216/Heckman/resources/02_Testing.zip)
  * [Dr. Heckman's Coverage and Static Analysis Lecture Notes](https://pages.github.ncsu.edu/engr-csc216/Heckman/slides/03_Coverage_StaticAnalysis.pdf)
  * [Guided Project 1 CourseTest.java](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/files/CourseTest.java)
  
Note that the tests for `Student` are similar to the [tests for `Course`](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/files/CourseTest.java) in Guided Project 1.  You may use those tests as examples and reference for Lab 2!
{% endcapture %}
{% include mention.html content=callout_content icon="ttTool" type="reminder" title="Reminder: Resources on Writing Tests" %}
## Testing Strategies
When testing POJOs, you want to ensure that we can construct them correctly and that changes to internal state through setters are handled correctly.  Additionally, you want to ensure that two objects are equal on the correct attributes and that the `toString()` method returns the correct comma-separated list of fields that are expected for writing to an output file.  `Student` should meet the [requirements defined in UC1](02-lab-requirements#uc1).

You should use our standard strategies of test the requirements, equivalence class partitioning, boundary value analysis, and basis set testing the method control flow to develop test cases.  The details below about each test method will help guide you as you develop your tests.

Your goal to to achieve at least 80% statement coverage by writing high quality tests that exercise most of the paths in your `Student` class.  There is 1 point of extra credit for exceeding 90% statement coverage, an additional point of extra credit for obtaining 100% statement coverage, and a third point of extra credit for achieving 100% condition coverage!

Make sure you run your tests frequently!  If you find a bug in your solution, fix it!





## Running Tests for Coverage
Before you start writing tests, make sure that you can run our tests instrumented for coverage.  Right click on the `test/` source folder and select **Coverage As > JUnit Test**.

When evaluating coverage locally, focus only on the coverage of `Student`, `StudentRecordIO`, and `StudentDirectory`.  The coverage of the test classes themselves and any user interface classes are not considered when evaluating the coverage of your tests.  Jenkins is set up to exclude test classes and user interface classes, but your local EclEmma is not.  Don't panic if the overall numbers seem low.

One last thing to check is that EclEmma is reporting the right metrics.  Click the triple dots or down arrow (View Menu) option in the **Coverage** view.  Select **Line Counters** for seeing statement/line coverage.  If you want to see condition coverage (for extra credit!), use the **Branch Counters** option.


## Testing `Student` Constructors
`Student` has two constructors: one that has parameters for all fields the other that has parameters for all fields but max credits.  The bullets below describe what each method should do and the sub-bullets describe what you should test!

`Student(String firstName, String lastName, String id, String email, String password, int maxCredits)`: calls the setters for each of the fields.  If the setters throw an `IllegalArgumentException`, the exception should pass through the constructor to the client.  That means the constructor does NOT catch the exception.  Just call the setters!
     
	 
  * Test that you can construct a valid `Student`.  This follows the strategy of testing requirements.  Make sure that you check all the fields are correct by using the getters.  If you want to assert on all the state of the object at once, see the examples in the [tests for `Course`](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/files/CourseTest.java) from GP1.
     
```java
assertEquals("first", s1.getFirstName());
```
     
	 
  * Start testing invalid input for each parameter - one at a time.  The standard structure of an invalid test is below.  You can also see examples in the [tests for `Course`](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/files/CourseTest.java) from GP1.
     
	 
	 
```java
Exception e1 = assertThrows(IllegalArgumentException.class,
				() -> new Student(.... parameters that would cause exception... );
assertEquals("Appropriate exception message", e1.getMessage());
```
     
`Student(String firstName, String lastName, String id, String email, String password)`: calls the other constructor with the default max credits value of 18.

  * Test in a similar manner to the other `Student` constructor.  The difference is that after calling this constructor, the `maxCredits` are always 18.


## Testing `Student` Getters
All getters for the `Student` fields are straightforward; they return the field.  Since the getters simply return the field, there is no need to write a distinct test method for the getters.  You've already tested them by testing the `Student` constructors!


## Testing `Student` Setters
The setters are more complex because they check to make sure that the `Student` fields are not invalid as defined in [[UC1]](01-lab-requirements#uc1).  If a value is invalid, an `IllegalArgumentException` should thrown.  You may be wondering why you're testing the setters after you've tested them through the `Student` constructors.  The reason is because while you may have achieved coverage through the constructors, you haven't tested that the setters work correctly AFTER an object is constructed.  You evaluate that in the setter test methods.

The strategy for testing the setters is the same for all the setters:

  1. Test that the setter works correctly by changing the valid value and making sure the change is there through calling a getter.
  
  2. Test that the setter throws an `IllegalArgumentException` when passed an invalid value using a structure similar to the one below:

```java
//Construct a valid Student
Student s = new Student("first", "last", "id", "email@ncsu.edu", "hashedpassword");
Exception e1 = assertThrows(IllegalArgumentException.class,
				() -> s.setFirstName(null);
assertEquals("Invalid first name", e1.getMessage()); //Check correct exception message
assertEquals("first", s.getFirstName()); //Check that first name didn't change
```

  * `setFirstName(String firstName)`: throws an `IllegalArgumentException` if the parameter is null or an empty string.
  * `setLastName(String lastName)`: throws an `IllegalArgumentException` if the parameter is null or an empty string.
  * `setId(String id)`: throws an `IllegalArgumentException` if the parameter is null or an empty string.  See the text below for a bit more info about `setId()`.
  * `setEmail(String email)`: throws an `IllegalArgumentException` if:
     * the parameter is null or an empty string
     * email doesn't contain an '@' character
     * email doesn't contain a '.' character
     * the index of the last '.' character in the email string is earlier than the index of the first '@' character (for example, first.last@address would be invalid)
  * `setPassword(String password)`: throws an `IllegalArgumentException` if the parameter is null or an empty string.
  * `setMaxCredits(int maxCredits)`: throws an `IllegalArgumentException` if the parameter is less than 3 or greater than 18.
  
Note that in the design, `setId()` is listed as a `private` method.  This is because a `Student`'s id shouldn't change after creation - it's the unique identifier in the `StudentDirectory`.  That means you can ONLY test `setId()` via the `Student()` constructor, which is the method that calls it.  If you've already covered `setId()` in your constructor tests, then you don't need a specific test method for `setId()`. Don't forget to make `setId()` private to meet the design!


## Testing `Student`'s `hashCode()` and `equals()`
The `Student` class has an `equals()` and `hashCode()` method generated by Eclipse. Assuming that you selected the correct fields when generating the methods, you can be pretty confident that `equals()` and `hashCode()` work correctly (lots of people use Eclipse and work on its code). However, you still need to test `equals()` and `hashCode()` to ensure greater than 80% statement coverage for full credit (or extra credit)!

The strategies for testing `equals()` and `hashCode()` are similar:

  * Create three or more objects. Two of the objects have the EXACT same state and the rest have at least one piece of different state.
  * For `equals()`, test that the two objects with the same state are equal and that two objects with different state are not equal.
  * For `hashCode()`, compare the generated hashcodes. `hashCode()` methods guarantee that if two objects are equal, they have the same hashcode.

Use the [Guided Project 1 CourseTest.testEquals() and CourseTest.testHashCode()]https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/files/CourseTest.java) methods as guides for writing your tests for `equals()` and `hashCode()`.

Note that achieving 100% statement or condition coverage for the `equals()` and `hashCode()` methods, as generated, is impossible with the `null` checks on `Student` fields during construction.  For example, the `email` field should never be `null`. You may modify the `equals()` and `hashCode()` methods to remove `null` checks to achieve 100% statement and condition coverage for extra credit!


## Testing `Student`'s `toString()`
The last item to test is `Student.toString()`. You want to make sure that the generated `String` is appropriate for output to the Student records file as per the [requirements](02-lab-requirements#uc1).

The steps for testing `toString()` are these:

  * Construct a valid `Student`.
  * Use the parameters to `Student` to create a `String` containing the expected comma-separated results.
  * Compare the expected results `String` to the `String` generated by `Student`.
  
This method was provided as part of Lab 01 and is included below to show how it matches the desription:

```java
/**
 * Test toString() method.
 */
@Test
public void testToString() {
	Student s1 = new Student(firstName, lastName, id, email, hashPW);
	assertEquals("first,last,flast,first_last@ncsu.edu," + hashPW + ",18", s1.toString());
}
```

## Run Your Tests
Run your tests instrumented for coverage.  Make sure that your tests execute at least 80% of the statements in `Student`.  Remember there is extra credit for more coverage!
  

## Javadoc your Code
Make sure that you Javadoc the `StudentTest` class, state (if any, including constants), and methods.  

Run [CheckStyle](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/gp1-static-analysis#checkstyle) to ensure that your Javadoc has all elements.

We DO expect that all test classes are commented!

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
At this point, your project should build on Jenkins with a Yellow exclamation point.  That is because you are not yet meeting coverage for `StudentRecordIO` and `StudentDirectory`.  Make sure there are no regressions of functionality from the teaching staff tests. If there are, use the feedback to go back and fix your code (and maybe your tests).


