# Lab Report 5: EdStem Post

## Title: Failed test for reverseInPlace
Hi, I wrote a method for reversing a list in place but it failed in tests, can someone help me to understand my error message?
my code:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
my test input:
```
public class ArrayTests {
  @Test 
	public void testReverseInPlace() {
    int[] input1 = {1, 2, 3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3, 2, 1}, input1);
	}
  @Test 
	public void testReverseInPlace2() {
    int[] input2 = {3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3}, input2);
	}
}
```
My error message: 
![Image](lab3a.png)	
Thank you!

---

**TA:** 
> Hi there,
> As a hint, I would suggest you to read through the returned messages. Could you > try printing the intermediate states of your array inside the loop to see what > values are being assigned? This might help you identify the issue.

---

**Student:**
I see! I noticed {symptoms...}
And I found that the bug is that the function overwrites the original elements of the array while performing the reversal. 

4. File & directory needed:
- The contents of each file before fixing the bug:
given in the inital post, `ArrayExamples.java` storing the method, `ArrayTest.java` storing the 2 test cases.
![Image](lab5a.png) 
![Image](lab5b.png)	

- The full command line to trigger the bug:
- A description of what to edit to fix the bug:
* **Before**: 
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
