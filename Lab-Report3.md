# Lab Report 3
## Part 1
Failure inducing intput:
```
@Test 
public void testReverseInPlaceMultiple(){
    int[] arr = {23, 32, 1};
    ArrayExamples.reverseInPlace(arr);
    assertArrayEquals(new int[]{1,32,23}, arr);
}
```
<br>
An input that doesn't induce failure:
```
@Test 
public void testReversedInPlaceSame(){
    int[] arr = {0, 0, 0, 0};
    ArrayExamples.reverseInPlace(arr);
    assertArrayEquals(new int[]{0,0,0,0}, arr);
}
```
<br>
Symptom of bug:
![image](Symptom.jpg)
<br>
The buggy method before:
```
// Changes the input array to be in reversed order
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
}
```
<br>
The buggy method after:
```
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    int[] temp = new int[arr.length];
    int k = 0;
    for(int i = arr.length-1; i >= 0; i--){
      temp[i] = arr[k];
      k++;
    }
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = temp[i];
    }
  }
```
<br>
My fix adresses the issue by storing all of the elements in a seperate array so no element is lost. The orginal method loses some of the elements by copying elements directly over to the other side of the array.

## Part 2 - The "grep" command options
<br>
The "-l" arguement in the grep command only lists the file names that contian the found lines. Found from: https://www.geeksforgeeks.org/grep-command-in-unixlinux/
<br>
Example 1:
```
timet@Bens-xps15 MINGW64 ~/Desktop/CSE_15l/LabReport3/docsearch/technical (main)
$ grep -l "e" *
grep: 911report: Is a directory
grep: biomed: Is a directory
grep: government: Is a directory
grep: plos: Is a directory
```
Example 2:
```
timet@Bens-xps15 MINGW64 ~/Desktop/CSE_15l/LabReport3/docsearch/technical/911report (main)
$ grep -l "e" *
chapter-1.txt
chapter-10.txt
chapter-11.txt
chapter-12.txt
chapter-13.1.txt
chapter-13.2.txt
chapter-13.3.txt
chapter-13.4.txt
chapter-13.5.txt
chapter-2.txt
chapter-3.txt
chapter-5.txt
chapter-6.txt
chapter-7.txt
chapter-8.txt
chapter-9.txt
preface.txt
```
<br>
This command is searching for all of the files that contian the given string. It can even print out the directories that contian the string. This is useful if you only want to know the files or directories that contian what your looking for and are not concered with their contents.

<br>
The "-o" option only prints the parts of the file that match the given line and what file that line is in. Found from: https://www.geeksforgeeks.org/grep-command-in-unixlinux/
<br>
Example 1:
```
timet@Bens-xps15 MINGW64 ~/Desktop/CSE_15l/LabReport3/docsearch/technical/911report (main)
$ grep -o "fast" *
chapter-1.txt:fast
chapter-1.txt:fast
chapter-1.txt:fast
chapter-11.txt:fast
chapter-12.txt:fast
chapter-13.1.txt:fast
chapter-13.1.txt:fast
chapter-3.txt:fast
chapter-3.txt:fast
chapter-6.txt:fast
chapter-6.txt:fast
chapter-6.txt:fast
```
Example 2:
```
timet@Bens-xps15 MINGW64 ~/Desktop/CSE_15l/LabReport3/docsearch/technical/911report (main)
$ grep -o "zzz" *
```
<br>
This command prints out the file name that matches the given string and prints out the contents of the file that matches the string. This could be useful for seeing what specifically matches inside of the files.

<br>
The "-h" option does not show the file name and only shows the matched lines. Found from: https://www.geeksforgeeks.org/grep-command-in-unixlinux/
<br>
Example 1:
```
timet@Bens-xps15 MINGW64 ~/Desktop/CSE_15l/LabReport3/docsearch/technical/biomed (main)
$ grep -h "is not very" *
        adjusted for all covariates, is not very different (the
          The phyletic pattern of the CYTH domain is not very
        receptors. Plasmid DNA alone is not very efficient
        ballpark X over the past month. This average is not very
          protonated Schiff base. This is not very different from λ
          relationship between subunits is not very flexible. The
          reaction being catalyzed is not very demanding, or if the
```
Example 2:
```
timet@Bens-xps15 MINGW64 ~/Desktop/CSE_15l/LabReport3/docsearch/technical/biomed (main)
$ grep -h "catch" *
        determined by Scatchard analysis with ELISA binding assays
          catch-all "don't know" category, rather than as a
          midline catches up to that in other areas of the
          catch-up after randomization. The time
          catch-up is the time when the number
          (catches-up to) the number of cases in the intervention
          catch-up only dilute the estimated
          catch-up does not occur if there is
          catch-up might not occur for a very
          Obrero hospital catchment areas were more well-to-do than
          Scatchard type binding described by:
          single site Scatchard type binding equation (see [ 1 ]
          Scatchard binding equation (eq. 3) must be used. This
            and resided within the HMO catchment area (see
          based on comparability with the hypothetical catchment
          or that fall into one of the catch-all subfamilies (such
```
<br>
This command is priniting out only the lines that contian the given search querery, not the file names. This could be useful if you are only concered with the lines of content that match and do not care about the file names.
