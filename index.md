
# Part 1
---
This is from the `ArrayExamples.java` java file and under the method `static void reverseInPlace(int[] arr)`

**A failure-inducing input**

```
@Test 
public void testReverseInPlace() {
    int[] input1 = { 3, 5 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 5, 3 }, input1);
}
```

**An input that doesn’t induce a failure**
```
@Test 
public void testReverseInPlace() {
    int[] input1 = { 9 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 9 }, input1);
}
```

**The symptom**

![Image](failtest.png)
![Image](passestest.png)


**The bug**

Before:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
}
```


After:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < (arr.length / 2); i += 1) {
      int placeHolder = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = placeHolder;
    }
}

```
For this piece of code, I added the `(arr.length / 2)` and `int placeHolder = arr[i];` as well as `arr[arr.length - i - 1] = placeHolder;`. `(arr.length / 2)` is to ensure that the iterated value falls properly in its place; continuing to iterate the value would just take you to the original input from `@Test`. Creating a holding variable such that it holds or takes into memory the array and storing that information in that same array. 


# Part 2: `find` command
---

1. `find /path/ -type f` or `-type d` command
   
   For `find /path -type f`
   
```
   $ find technical/government/About_LSC/ -type f
technical/government/About_LSC/Comments_on_semiannual.txt
technical/government/About_LSC/commission_report.txt
technical/government/About_LSC/conference_highlights.txt
technical/government/About_LSC/CONFIG_STANDARDS.txt
technical/government/About_LSC/diversity_priorities.txt
technical/government/About_LSC/LegalServCorp_v_VelazquezDissent.txt
technical/government/About_LSC/LegalServCorp_v_VelazquezOpinion.txt
technical/government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt
technical/government/About_LSC/ODonnell_et_al_v_LSCdecision.txt
technical/government/About_LSC/ONTARIO_LEGAL_AID_SERIES.txt
technical/government/About_LSC/Progress_report.txt
technical/government/About_LSC/Protocol_Regarding_Access.txt
technical/government/About_LSC/reporting_system.txt
technical/government/About_LSC/Special_report_to_congress.txt
technical/government/About_LSC/State_Planning_Report.txt
technical/government/About_LSC/State_Planning_Special_Report.txt
technical/government/About_LSC/Strategic_report.txt

source: https://www.znetlive.com/blog/how-to-use-linux-find-command-to-search-for-files/#:~:text=Whether%20you%20need%20to%20locate,tools%20to%20accomplish%20these%20tasks.&text=Here%2C%20the%20%2Dtype%20f%20option,or%20other%20types%20of%20files.

```
  For `find /path/ -type d`
  
```
$ find technical/ -type d
technical/
technical/911report
technical/biomed
technical/government
technical/government/About_LSC
technical/government/Alcohol_Problems
technical/government/Env_Prot_Agen
technical/government/Gen_Account_Office
technical/government/Media
technical/government/Post_Rate_Comm
technical/plos

source: https://www.znetlive.com/blog/how-to-use-linux-find-command-to-search-for-files/#:~:text=Whether%20you%20need%20to%20locate,tools%20to%20accomplish%20these%20tasks.&text=Here%2C%20the%20%2Dtype%20f%20option,or%20other%20types%20of%20files.
```
