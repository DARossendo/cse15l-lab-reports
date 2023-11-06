
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


# Part 2: `find` Command
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

This type of find essentially takes the .txt files from the directory or the directories within the directories and prints its content depending on `-type f` or `=type d`. This is useful for when we want to find only files or only want directories.

2. `find /path/ -size +M` or `-type d`

For `find /path/ -size +M`

```
find technical/government/Env_Prot_Agen/  -size +100k
technical/government/Env_Prot_Agen/bill.txt
technical/government/Env_Prot_Agen/ctm4-10.txt
technical/government/Env_Prot_Agen/multi102902.txt
technical/government/Env_Prot_Agen/tech_adden.txt

source: https://www.znetlive.com/blog/how-to-use-linux-find-command-to-search-for-files/#:~:text=Whether%20you%20need%20to%20locate,tools%20to%20accomplish%20these%20tasks.&text=Here%2C%20the%20%2Dtype%20f%20option,or%20other%20types%20of%20files.
```

For ` find /path/ -type d -size +M`

```
find technical/ -type d -size -30M
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

This command essentially considers all the files with `-type f` or `-type d`, checks the sizes ranging from bytes to megabytes and prints when given the parameters. This is useful when we want to detect directories of files that consist of too much space.

3. `find /path -name "[filename.txt]" -exec [command] {} [extra info];` or `find /path -type d -name "[directory_name]" -exec [command] {} [extra info];`

For `find /path -name "[filename.txt]" -exec [command] {} [extra info];`
```
find technical/911report/ -name "chapter-1.txt" -exec cp {} backup/ \;

Source: https://www.geeksforgeeks.org/exec-command-in-linux-with-examples/#
Source: https://www.baeldung.com/linux/find-exec-command

```

For `find /path -type d -name "[directory name]" -exec [command] {} [extra info];`

```
find technical/ -type d -name "biomed" -exec cp -r {} test2 \;

Source: https://www.geeksforgeeks.org/exec-command-in-linux-with-examples/#
Source: https://www.baeldung.com/linux/find-exec-command
```

This command essentially gives a path with either name being the file or directory and gives an `-exec` executable command to perform with any given parameters; here I use cp to copy files. This command is useful when we want to perform one-line executables.

4. `find /path -maxdepth 1 -type f` or `-type d`

For `find /path -maxdepth 1 -type f`

```
$ find technical/911report/ -maxdepth 1 -type f
technical/911report/chapter-1.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
technical/911report/chapter-12.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-2.txt
technical/911report/chapter-3.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-8.txt
technical/911report/chapter-9.txt
technical/911report/preface.txt

source: https://www.geeksforgeeks.org/mindepth-maxdepth-linux-find-command-limiting-search-specific-directory/
```

For `find /path -maxdepth 1 -type d`

```
$ find technical/ -maxdepth 1 -type d
technical/
technical/911report
technical/biomed
technical/government
technical/plos

source: https://www.geeksforgeeks.org/mindepth-maxdepth-linux-find-command-limiting-search-specific-directory/
```
The `-maxdepth 1` command allows restricting to the immediate directory without branching to other directories. It's useful when it comes to specifying how far must you go to find files and directories. 












