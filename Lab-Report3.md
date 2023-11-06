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

