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

## Part 2
The "grep" command options
