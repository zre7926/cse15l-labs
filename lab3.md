Lab Report 3 - Bugs and Commands (Week 5)
========
Ryan Zhang <br> A17852116

Part 1
--------
Failure inducing input:
```
@Test
public void testReversed() {
  int[] input1 = {1,2,3};
  assertArrayEquals(new int[]{3,2,1}, ArrayExamples.reversed(input1));
}
```
Input that doesn't induce a failure:
```
@Test
public void testReversed() {
  int[] input1 = {0};
  assertArrayEquals(new int[]{0}, ArrayExamples.reversed(input1));
}
```
Running the second input: 
```
(base) ryanz@Ryan-4 lab3 % javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
(base) ryanz@Ryan-4 lab3 % java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
..
Time: 0.004

OK (2 tests)
```
Running the first input:
```
(base) ryanz@Ryan-4 lab3 % javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
(base) ryanz@Ryan-4 lab3 % java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
..E
Time: 0.004
There was 1 failure:
1) testReversed(ArrayTests)
arrays first differed at element [0]; expected:<3> but was:<0>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReversed(ArrayTests.java:15)
        ... 30 trimmed
Caused by: java.lang.AssertionError: expected:<3> but was:<0>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 36 more

FAILURES!!!
Tests run: 2,  Failures: 1
```

Before fixing the bug:
```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = newArray[arr.length - i - 1];
  }
  return arr;
}
```

After fixing the bug:
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```
To fix the bug, I changed the line inside the for loop and the return statement. The problem with the original code is that it changes and returns the original array instead of the newly-created array.
Therefore, by changing the code to alter and return the newly created array, the bug is successfully fixed. <br>

Part 2
--------
In this part, I will explore the different command-line options to use the `find`command
1. search by name
```
(base) ryanz@Ryan-4 docsearch % find . -name "ar79.txt"
./technical/biomed/ar79.txt
```
This command searches the `docsearch` directory for a file or folder with the name `ar79.txt` and gives its path if found.

```
(base) ryanz@Ryan-4 docsearch % find . -name "plos"
./technical/plos
```
This command searches the `docsearch` directory for a file or folder with the name `plos` and gives its path if found.<br><br>
This option is useful when you are looking for a file or folder with a known name through a bunch of files and folders.
<br>

2. search by name in given directory
```
(base) ryanz@Ryan-4 docsearch % find technical/biomed/ -name "ar79.txt"
technical/biomed//ar79.txt
```
This command searches the `docsearch/technical/biomed/` directory for a file with the name `ar79.txt` and gives its path if found.

```
(base) ryanz@Ryan-4 docsearch % find technical/ -name "plos"
technical//plos
```
This command searches the `docsearch/technical/` directory for a file with the name `plos` and gives its path if found.<br><br>
This option is useful when you are looking for a file or folder with a known name in a specific directory.
<br>

3. search file by name and then delete
```
(base) ryanz@Ryan-4 docsearch % find . -name chapter-12.txt -delete
```
This command searches the `docsearch` directory for a file with the name `chapter-12.txt` and deletes it if found.

```
(base) ryanz@Ryan-4 docsearch % find . -name journal.pbio.0020001.txt -delete
```
This command searches the `docsearch` directory for a file with the name `journal.pbio.0020001.txt` and deletes it if found.<br><br>
This option is useful when you are trying to delete a file when you don't know where it is but know its name.
<br>

4. search by directory and type
```
(base) ryanz@Ryan-4 docsearch % find ./technical/ -type d 
./technical/
./technical//government
./technical//government/About_LSC
./technical//government/Env_Prot_Agen
./technical//government/Alcohol_Problems
./technical//government/Gen_Account_Office
./technical//government/Post_Rate_Comm
./technical//government/Media
./technical//plos
./technical//biomed
./technical//911report
```
This command searches the `docsearch/technical` drectory for directories and prints their paths out.

```
(base) ryanz@Ryan-4 docsearch % find ./technical/government/Post_Rate_Comm  -type f
./technical/government/Post_Rate_Comm/Gleiman_EMASpeech.txt
./technical/government/Post_Rate_Comm/Mitchell_spyros-first-class.txt
./technical/government/Post_Rate_Comm/Cohenetal_CreamSkimming.txt
./technical/government/Post_Rate_Comm/Cohenetal_DeliveryCost.txt
./technical/government/Post_Rate_Comm/Mitchell_RMVancouver.txt
./technical/government/Post_Rate_Comm/Gleiman_gca2000.txt
./technical/government/Post_Rate_Comm/Cohenetal_Cost_Function.txt
./technical/government/Post_Rate_Comm/Redacted_Study.txt
./technical/government/Post_Rate_Comm/Mitchell_6-17-Mit.txt
./technical/government/Post_Rate_Comm/Cohenetal_comparison.txt
./technical/government/Post_Rate_Comm/Cohenetal_Scale.txt
./technical/government/Post_Rate_Comm/Cohenetal_RuralDelivery.txt
./technical/government/Post_Rate_Comm/ReportToCongress2002WEB.txt
./technical/government/Post_Rate_Comm/WolakSpeech_usps.txt
```
This command searches the `docsearch/technical/government.Post_Rate_Comm` drectory for files and prints their paths out.<br><br>
This option is useful when you are trying to find a certain kind of file.
<br>

Citation: https://www.linuxteck.com/find-command-in-linux-with-examples/




