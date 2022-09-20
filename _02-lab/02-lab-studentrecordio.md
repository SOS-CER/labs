---
title: CSC 217 Lab 02 - Software Engineering Best Practices
tags: [software engineering, software lifecycle, CS2, CSC 217, Lab02]
description: Unit Test `StudentRecordIO`
navigation: on
pagegroup: 02-lab
---

`StudentRecordIO` provides `static` methods that support reading in student records from a file and writing student records to a file.  A student record is defined in the requirements [Data Format](02-lab-requirements#data-format).  The read functionality is defined in [[UC3]](02-lab-requirements#uc3) and the write functionality is defined in [[UC4]](02-lab-requirements#uc4).

{% include iconHeader.html type="unitTest" %}

Since the methods of `StudentRecordIO` are `static`, `StudentRecordIO` doesn't require a defined constructor.  There is a constructor listed in the design, but that is the default constructor that all classes have.  You do NOT need to define a constructor for `StudentRecordIO`.  There is no state to initialize.

You will test the `StudentRecordIO` class using the files provided in the `test-files` directory.

 
## Create a `StudentRecordIOTest` Class
To create the `StudentRecordIOTest` class, do the following:

  * Right click on `StudentRecordIO` and select **New > JUnit Test Case**. 
  * Change the **Source folder** to `/PackScheduler/test`.  Click **Next**.
  * Select the `StudentRecordIO` methods `readStudentRecords()` and `writeStudentRecords()`.  Additionally, check the option to create a `setUp()` method.  You'll use this a helper for setting up input files.  Click **Finish**.
  * A new class `StudentRecordIOTest` will be created in the `edu.ncsu.csc216.pack_scheduler.io` package in the `test/` source folder that will contain empty test methods for the `StudentRecordIO` methods.  You will work with getters of `Student` objects to make sure that `StudentRecordIO` is working correctly.
  
If the `StudentRecordIOTest` file isn't in the right package or source folder, move it to the appropriate location.  If it's not in the right place, your tests may not be executed on Jenkins!


{% capture callout_content %}
There are several resources provided for writing tests, including sample test code:

  * [Testing Packet](https://pages.github.ncsu.edu/engr-csc116-staff/CSC116-Materials/testing/version/6.0.0/)
  * [Dr. Heckman's Testing Lecture Notes](https://pages.github.ncsu.edu/engr-csc216/Heckman/slides/02_TestingDebugging.pdf)
  * [Seasons Test Example](https://pages.github.ncsu.edu/engr-csc216/Heckman/resources/02_Testing.zip)
  * [Dr. Heckman's Coverage and Static Analysis Lecture Notes](https://pages.github.ncsu.edu/engr-csc216/Heckman/slides/03_Coverage_StaticAnalysis.pdf)
  * [Guided Project 1 CourseTest.java](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/files/CourseTest.java)
  
Note that the tests for `StudentRecordIO` are similar to the [tests for `CourseRecordIO`](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/files/CourseRecordIOTest.java) in Guided Project 1.  You may use those tests as examples and reference for Lab 2!
{% endcapture %}
{% include mention.html content=callout_content icon="ttTool" type="reminder" title="Reminder: Resources on Writing Tests" %}
## Testing Strategies
When testing file I/O, you will have input files, expected output files, and actual output files.  Helper methods in the test class provide functionality for ensuring that you're starting with a correct input file and for comparing expected and actual output files.  The helper methods are described further below.

You should use our standard strategies of test the requirements, equivalence class partitioning, boundary value analysis, and basis set testing the method control flow to develop test cases.  The details below about each test method will help guide you as you develop your tests.

Your goal to to achieve at least 80% statement coverage by writing high quality tests that exercise most of the paths in your `StudentRecordIO` class.  There is 1 point of extra credit for exceeding 90% statement coverage, an additional point of extra credit for obtaining at least 96% statement coverage (you'll never be able to cover the class b/c we don't directly construct it), and a third point of extra credit for achieving 100% condition coverage!

Make sure you are frequently running your tests!  If you find a bug in your solution, fix it!





## Test Files
There are two pieces of functionality that you're testing in `StudentRecordIO`: reading from a file and writing to a file.  All files that support testing `StudentRecordIO` are found in `test-files/`.  

The method `StudentRecordIO.readStudentRecords()` provides the functionality for reading from a file.  That means you need a test input file with valid records and a test input file with invalid records to support testing.  These are provided in `test-files/student_records.txt` and `test-files/invalid_student_records.txt`, respectively.  You'll use these files for testing `readStudentRecords()`.  The file `expected_full_student_records.txt` is provided so you can copy the contents of it to `student_records.txt` if something you do messes up your copy of `student_records.txt`,  you can also get a new copy from the [starter zip](../01-lab/files/PackScheduler.zip).

The method `StudentRecordIO.writeStudentRecords()` provides the functionality for writing to a file.  That means you need to compare the actual results of writing to a file that contains the expected results from writing.  A possible expected result from creating a single student record is in the `expected_student_records.txt` file.  You may update this file to reflect the expected results from your test.

When working in Eclipse, the project is your "present working directory".  That means the path to all files MUST be relative to your `PackScheduler` project.  When including file paths in your tests, include the path of `test-files/<file>`.


## File Testing Helper Methods
You can create several helper methods to support file I/O testing.  

The first helper method, `checkFiles()` compares the contents of two files to see if they are the same.  The method creates `Scanner`s for both files.  The parameter to `Scanner` is a `FileInputStream` that supports reading of hashed passwords.  However, for these tests, the passwords do not have to be hashed.  The method then compares the two files line by line.  If two corresponding lines are different, the test will fail.  If all the lines are the same, the test then checks to see if there are any additional lines in either `Scanner`.  If so, the test fails.  Both `Scanners` are closed.  If the `IOException` is thrown, there was a problem reading the files.  This may happen if too many other processes are trying to read the files at the same time or if the path to the file is incorrect in the tests.  Restarting Eclipse can help free file handles for testing.

```java
/**
 * Helper method to compare two files for the same contents
 * @param expFile expected output
 * @param actFile actual output
 */
private void checkFiles(String expFile, String actFile) {
	try (Scanner expScanner = new Scanner(new FileInputStream(expFile));
		 Scanner actScanner = new Scanner(new FileInputStream(actFile));) {
		
		while (expScanner.hasNextLine()  && actScanner.hasNextLine()) {
			String exp = expScanner.nextLine();
			String act = actScanner.nextLine();
			assertEquals(exp, act, "Expected: " + exp + " Actual: " + act); 
			//The third argument helps with debugging!
		}
		if (expScanner.hasNextLine()) {
			fail("The expected results expect another line " + expScanner.nextLine());
		}
		if (actScanner.hasNextLine()) {
			fail("The actual results has an extra, unexpected line: " + actScanner.nextLine());
		}
		
		expScanner.close();
		actScanner.close();
	} catch (IOException e) {
		fail("Error reading files.");
	}
}
```
    
The second helper method is the `setUp()` method.  You can use that to do several things to set up the files for testing before calling each method.  One thing you can do is copy the contents of `expected_full_student_records.txt` into `student_records.txt` in case something happens to the file during testing.  However, if you avoid writing to `student_records.txt`, you won't need this functionality.  

The second thing you could include is code to hash the password.  **You CANNOT store the password in Java source files as a `String` literal.  This is a security vulnerability!**  Instead, you need to programatically hash the password for each `Student` object you create for testing.  It turns out that all of the passwords in the provided test files are a hash of the `String` "pw" ("pw" is a HORRIBLE password.  We're only using it for testing.  You should NEVER use "pw" as an actual password on a production system!).  You can then store the hash of "pw" to a field for use in your tests.

In the code below, a `String` has been created for each of the students in the provided `student_records.txt` file.  When the `setUp()` method runs before each test, each substring `pw` will be replaced with the hashed value for "pw".  This value will match the hashed value that is in the `student_records.txt` file.  

```java
private String validStudent0 = "Zahir,King,zking,orci.Donec@ametmassaQuisque.com,pw,15";
private String validStudent1 = "Cassandra,Schwartz,cschwartz,semper@imperdietornare.co.uk,pw,4";
private String validStudent2 = "Shannon,Hansen,shansen,convallis.est.vitae@arcu.ca,pw,14";
private String validStudent3 = "Demetrius,Austin,daustin,Curabitur.egestas.nunc@placeratorcilacus.co.uk,pw,18";
private String validStudent4 = "Raymond,Brennan,rbrennan,litora.torquent@pellentesquemassalobortis.ca,pw,12";
private String validStudent5 = "Emerald,Frost,efrost,adipiscing@acipsumPhasellus.edu,pw,3";
private String validStudent6 = "Lane,Berg,lberg,sociis@non.org,pw,14";
private String validStudent7 = "Griffith,Stone,gstone,porta@magnamalesuadavel.net,pw,17";
private String validStudent8 = "Althea,Hicks,ahicks,Phasellus.dapibus@luctusfelis.com,pw,11";
private String validStudent9 = "Dylan,Nolan,dnolan,placerat.Cras.dictum@dictum.net,pw,5";

private String [] validStudents = {validStudent0, validStudent1, validStudent2, validStudent3, validStudent4, validStudent5,
        validStudent6, validStudent7, validStudent8, validStudent9};

private String hashPW;
private static final String HASH_ALGORITHM = "SHA-256";

@BeforeEach
public void setUp() {
    try {
        String password = "pw";
        MessageDigest digest = MessageDigest.getInstance(HASH_ALGORITHM);
        digest.update(password.getBytes());
        hashPW = Base64.getEncoder().encodeToString(digest.digest());
        
        for (int i = 0; i < validStudents.length; i++) {
            validStudents[i] = validStudents[i].replace(",pw,", "," + hashPW + ",");
        }
    } catch (NoSuchAlgorithmException e) {
        fail("Unable to create hash during setup");
    }
}
```


{% capture callout_content %}
We don't want to store student passwords in plain text.  Instead we are using a hashing algorithm to transform the student passwords into a string of unreadable text.  Hashes are one way transformations of a plain text string to a garbled/hashed version.  There isn't an algorithm to transform the hashed string back to the plain text string.  Later when we start checking passwords for authentication, we'll compare the hashes.

We are using SHA-256 as our hash algorithm.  We pass in the password as bytes, which is the underlying binary representation of the password string.  We then encode the string using Base64.  This presents the hashed password using the [Base64 alphabet (see Table 1)](https://www.ietf.org/rfc/rfc4648.txt).  This means that the string utilizes characters that are consistent when opening the student files and using various text editors.  

Because you are working with hashed character strings, using a `File` parameter to the `Scanner` object is not sufficient.  The hashes are really bytes of data; not a string you would read.  So instead of using a `File` parameter, you should [instead use a `FileInputStream`](https://docs.oracle.com/javase/8/docs/api/java/io/FileInputStream.html).  `FileInputStream` lets you read the input file as a series of bytes rather than a series of characters.  After the `Scanner` is created using the `FileInputStream`, you can work with the `Scanner` as you are used to.
{% endcapture %}
{% include callout.html content=callout_content icon="plTool" type="conceptualKnowledge" title="Conceptual Knowledge: Reading Hashed Strings" %}
    

## Testing `readStudentRecords(String)` 
`readStudentRecords(String fileName)` will read in `Student` records from the file represented by the given `fileName`.  The records are returned in an `ArrayList<Student>` in a very similar manner to [`CourseRecordIO.readCourseRecords()` from GP1](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/gp1-libraries#java-collections-framework).  The method will throw a `FileNotFoundException` if the file does not exist on the file system. 

Your tests should evaluate the following:

  * That the correct number of `Student`s are read in from `student_records.txt` and that they are stored in the `ArrayList` of `Student`s in the right order and with the correct state.  You compare the state by comparing the `String` stored in the `validStudents` array with the result of the call to `Student.toString()` for each `Student`.
  * That no `Student`s are read in from `invalid_student_records.txt`.  The `ArrayList` should be empty.
  * That a `FileNotFoundException` is thrown if the method is passed a file that doesn't exist.


## Testing `writeStudentRecords(String)`
`writeStudentRecords(String fileName, ArrayList<Student> studentDirectory)` will write the `Student`s in `studentDirectory` to the file represented by the `fileName` one `Student` record at a time.  The records are written in a very similar manner to [`CourseRecordIO.writeCourseRecords()` from GP1](https://pages.github.ncsu.edu/engr-csc216/guided-projects/gp1/gp1-libraries#file-output).  The method will throw an `IOException` if unable to write to the file.

Your test should evaluate the following:

  * That writing a list of `Student`s to the file results in the expected output.
  * That an `IOException` is thrown if you cannot write to a file.
  
You have to be clever about how you write a test for the `IOException`.  A file write fails for two reasons: 1) you do not have permission to write to the directory or 2) the system is out of space.  The second option shouldn't happen because of the large space we have on the system and the protections we have in place to prevent consumption of all space.  The first option is the best bet.  The best way to achieve this test is to attempt to write to a portion of the file system you do not have access to.  You may use the path `/home/sesmith5/actual_student_records.txt` for your test on Jenkins.  If you are using Windows, this test will fail due to a different error message because of the / in the path.  It may fail on Mac and Linux because the file is actually created, so you may want to clean up the folders/file created if it does pass.  It WILL pass on Jenkins (which is where we are grading you).

```java
@Test
public void testWriteStudentRecordsNoPermissions() {
	ArrayList<Student> students = new ArrayList<Student>();
	students.add(new Student("Zahir", "King", "zking", "orci.Donec@ametmassaQuisque.com", hashPW, 15));
	
	Exception exception = assertThrows(IOException.class, 
			() -> StudentRecordIO.writeStudentRecords("/home/sesmith5/actual_student_records.txt", students));
	assertEquals("/home/sesmith5/actual_student_records.txt (No such file or directory)", exception.getMessage());
}
```


## Run Your Tests
Run your tests instrumented for coverage.  Make sure that your tests execute at least 80% of the statements in `StudentRecordIO`.  Remember there is extra credit for more coverage!

If the `testWriteStudentRecordsNoPermissions()` fails locally, it won't record the coverage.  Push to GitHub and run on Jenkins to verify coverage of throwing that exception.  Note that Jenkins will say there is no coverage of the `StudentRecordIO()` constructor.  Since you are working with the class statically, the constructor will never be called.  That will not be counted against you.
    

## Javadoc your Code
Make sure that you Javadoc the `StudentRecordIOTest` class and methods. 

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
At this point, your project should build on Jenkins with a Yellow "!".  That is because you are not yet meeting coverage for `StudentDirectory` (the provided tests likely won't meet the coverage requirements).  Make sure there are no regressions of functionality from the teaching staff tests. If there are, use the feedback to go back and fix your code (and maybe your tests).


