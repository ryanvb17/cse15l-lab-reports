#Lab Report 2

##Part 1
Code:
add code

Messages:
add messages

For both messages handleRequest is called, with the relevant field str and parameter url.
For the first message str gets changed from "" to "Hi", while the second one changes it from "Hi" to "Hi\nWhat's up?".
In the first message url is "http://localhost:3500/add-message?s=Hi" while the second has a url of "http://localhost:3500/add-message?s=What%27s%20up?".

##Part 2
For ArrayExamples.java:
  @test
  public void testReverseInPlace() {
    int[] test = {1,2,3,4,5}
    ArrayExamples.reverseInPlace(test);
    assertArrayEquals(new int[]{5,4,3,2,1}, test);
  }
  
  @test
  public void testReverseInPlace() {
    int[] test = {1,1,1,1,1}
    ArrayExamples.reverseInPlace(test);
    assertArrayEquals(new int[]{1,1,1,1,1}, test);
  }
  
SS of code running
  
The bug is that the array will write over the old values in the second half of the array with the new ones from the first half,
which are often going to be different from what they were in the beginning.

Before:
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }

After:
  static void reverseInPlace(int[] arr) {
  int[] copy = arr;
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = copy[copy.length - i - 1];
    }
  }
Using a copy of the array allows the values in the second-half of the array to switch with the old values from the first half.
  
  
  

##Part 3
In lab 2 I learned how to build a basic server, which was fun to learn about. 
I didn't expect to be able to change values so easily just by updating the url,
so I was pretty excited to be able to mess around with that feature.
