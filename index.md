
#Part 1
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

```
@Test 
public void testReverseInPlace() {
    int[] input1 = { 9 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 9 }, input1);
}
```
