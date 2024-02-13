## Bug: reverseInPlace
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
## correct version:
```
static void reverseInPlace(int[] arr) {
    for (int i = 0; i < arr.length / 2; i++) {
        // Swap elements at i and arr.length - i - 1
        int temp = arr[i];
        arr[i] = arr[arr.length - i - 1];
        arr[arr.length - i - 1] = temp;
    }
}
```
## Failure-inducing
```
public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
    int[] input1 = {1, 2, 3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3, 2, 1}, input1);
	}
```
## Input that does not induce a failure
```
  @Test 
	public void testReverseInPlace2() {
    int[] input1 = {3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3}, input1);
	}
}
```
*The symptom of the function reverseInPlace:
![sca](lab3a.png)

*The bug is that the function overwrites the original elements of the array while performing the reversal. To address the bug, modifications need to be made within the for-loop:
* **Before**: The assignment ```arr[i] = arr[arr.length - i - 1]; ```replaces each element with its corresponding element from the reversed position.
```
      for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  ```
* **After**: 
```
    for (int i = 0; i < arr.length / 2; i++) {
        int temp = arr[i];
        arr[i] = arr[arr.length - i - 1];
        arr[arr.length - i - 1] = temp;
}
```
* **Explaination**: In this corrected version, a temp variableis used to store the element being swapped, The loop runs only half the length of the array, swapping elements from both ends and moving towards the center. 

# Part 2
## **Find**

1. ```-name```: Searches for files and directories with the specified name.
Example 1:
```
[user@sahara ~]$ cd docsearch/technical/
[user@sahara ~/docsearch/technical]$ find -name 911*
./911report
```
Example 2:
```
[user@sahara ~/docsearch/technical]$ find ./911report -name "chapter-1.txt"
./911report/chapter-1.txt
```
2. ```-type```: Filters results based on the type of file (e.g., regular file, directory, symbolic link).
Example 1:
```
[user@sahara ~/docsearch/technical]$ find -type d
.
./biomed
./911report
```
Example 2:
```
[user@sahara ~/docsearch/technical]$ find ./911report -type f
./911report/chapter-8.txt
./911report/chapter-13.3.txt
./911report/chapter-10.txt
./911report/chapter-13.5.txt
./911report/chapter-11.txt
./911report/chapter-7.txt
./911report/chapter-13.4.txt
./911report/chapter-13.2.txt
./911report/chapter-5.txt
./911report/chapter-13.1.txt
./911report/chapter-3.txt
./911report/chapter-2.txt
./911report/chapter-6.txt
./911report/chapter-9.txt
./911report/preface.txt
./911report/chapter-1.txt
./911report/chapter-12.txt
```
3. ```-mtime```: Finds files based on their modification time in days.
Example 1:
```
[user@sahara ~/docsearch/technical]$ find -mtime -1 -name "chapter-1.txt"
./911report/chapter-1.txt
```
(to find files modified within the last 1 day and file name as "chapter-1.txt").
Example 2:
```
./911report/chapter-1.txt
[user@sahara ~/docsearch/technical]$ find ./911report -mtime -5
./911report
./911report/chapter-8.txt
./911report/chapter-13.3.txt
./911report/chapter-10.txt
./911report/chapter-13.5.txt
./911report/chapter-11.txt
./911report/chapter-7.txt
./911report/chapter-13.4.txt
./911report/chapter-13.2.txt
./911report/chapter-5.txt
./911report/chapter-13.1.txt
./911report/chapter-3.txt
./911report/chapter-2.txt
./911report/chapter-6.txt
./911report/chapter-9.txt
./911report/preface.txt
./911report/chapter-1.txt
./911report/chapter-12.txt
```
(to find all files modified within the last 5 day within directory 911report).

4. ```-iname```: Allows a case-insensitive search, so it matches files with names like "Pattern.txt" or "PATTERN.txt."
Example 1: 
```
[user@sahara ~/docsearch/technical]$ find -iname "911REPORT"
./911report
```
Example 2:
```
[user@sahara ~/docsearch/technical]$ find ./911report -iname "ChAPteR-1.txt"
./911report/chapter-1.txt
```
*above commands are from ChatGPT, my given prompt: Can you give me some examples of command-line options for ```find```?
