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
Example: find /path/to/search -name "filename.txt"
2. ```-type```: Filters results based on the type of file (e.g., regular file, directory, symbolic link).
Example: find /path/to/search -type d (to find directories).
3. ```-mtime```: Finds files based on their modification time in days.
Example: find /path/to/search -mtime -7 (to find files modified within the last 7 days).
4. ```-exec```: Executes a command on the found files or directories.
Example: find /path/to/search -name "*.txt" -exec rm {} \; (to delete all text files found).

*above commands are from ChatGPT, my given prompt: Can you give me some examples of command-line options for ```find```?
