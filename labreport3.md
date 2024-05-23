Given this method:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
Then, given these two tests:
```
public class ArrayTests2 {
	@Test 
	public void testReverseInPlaceTwo() {
    int[] input1 = { 1, 2 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 2, 1 }, input1);
	}

    @Test 
	public void testReverseInPlaceOne() {
    int[] input1 = { 1 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 1 }, input1);
	}
}
```
The first test fails, while the second test doesn't:
![Symptom_Image](Symptom.png)

And given this the orginal code:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
Changed it to:
```
static void reverseInPlaceNew(int[] arr) {
    for(int i = 0; i < arr.length / 2; i += 1) {
      int holder = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = holder;
    }
  }
```
This now stops the previous code from creating a mirrored array, but instead a properly reversed one.
