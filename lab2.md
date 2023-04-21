Lab Report 2 - Servers and Bugs - April 24, 2023
================================================

Part 1 - StringServer Website
---

I created code that I have reasonable confidence in, but I am unable to run it, as when I launch it as a server,  the server itself functions as the NumberServer
we worked on during lab 2. I posted a problem about this on edstem, it is number #107. If this is still here upon submission, I have yet to figure out the issue
I am having.

Part 2 - Testing from Lab 3
---
s
The buggy method I want to cover for this lab report is the `reversed` method in `ArrayExamples`.

One failure inducing input that I found was:

    @Test
    public void testReversed313() {
      int[] input1 = {3, 1, 3,};
      assertArrayEquals(new int[]{3, 1, 3}, ArrayExamples.reversed(input1));
    }
  
  
  
One non-failure inducing input that I found was: 

    @Test
    public void testReversed00000() {
      int[] input1 = {0, 0, 0, 0, 0};
      assertArrayEquals(new int[]{0, 0, 0, 0, 0}, ArrayExamples.reversed(input1));
    
    }
    
    
The symptom of the failure inducing input is shown by the output after running jUnit:
 
![Both tests after running](https://rnguerrero.github.io/cse15l-lab-reports/Lab3%20Pics/12341234.png)
  
  
This is how the `reversed` method looked like before I made the bug fixes:

    static int[] reversed(int[] arr) {
        int[] newArray = new int[arr.length];
        for(int i = 0; i < arr.length; i += 1) {
            arr[i] = newArray[arr.length - i - 1];
        }
        return arr;

And this is how it looks after I made the bug fixes:

    static int[] reversed(int[] arr) {
        int[] newArray = new int[arr.length];
        for(int i = 0; i < arr.length; i += 1) {
            newArray[i] = arr[arr.length - i - 1];
        }
        return newArray;

The change I made was changing the array that is being changed from `arr`, which is the array that represents the argument for the method, to `newArray`, which is the blank array that was created within the method. This change does two things: 

- Changes the newly created array (`newArray`) instead of the arry in the argument (`arr`) 
- Copies the elements of `arr` to `newArray`, which is the array that is returned.
  
