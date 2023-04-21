Lab Report 2 - Servers and Bugs - April 24, 2023
================================================
---
Part 1 - StringServer Website
---

I created code that I have reasonable confidence in, but I am unable to run it, as when I launch it as a server,  the server itself functions as the NumberServer
we worked on during lab 2. I posted a problem about this on edstem, it is number #107. If this is still here upon submission, I have yet to figure out the issue
I am having.

---
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
- Copies the elements of `arr` to `newArray` in reverse order, which is the array that will be returned.
  
It is important that the newly created array is the only thing that is edited because that is what the method is intended to do, according to the note above said method. ("Returns a *new* array with all the elements of the input array in reversed order") 
When `newArray` is created, none of its elements are defined, so they get set to a default value. Since it is an int[] array, the default values are `0`s. That is why jUnit says that we expected `3` at index `0`, but actually got `0`. When `newArray` and `arr` are switched, `newArray` has every one of its elements changed to one of `arr`'s indexes, specifically the `[arr.length - i - 1]`th index, where i represents the `newArray` index.

All-in-all, this change goes from making the output all `0`s, to `arr` in reverse order, as desired.


---
Part 3 - What I've learned

To cap off this lab report, I feel like I've learned a lot during these past two weeks. I suppose the most valuable thing I learned was about the nature of jUnit. I have heard of it, and continue to interact with it due to its prominence in CSE12, but we never got answers as to how it worked, leaving me with questions such as 'Why is it so different from checkExpect, which we used in cse 8B?', 'Why do we use eclipse for our programing assignments instead of VSC,' and 'Why are the PAs so differently formated?', but thanks to the recent lecture and labs, I now understand better the nature of jUnit as an external library, or a library that is not from a java library, so actually executing the tests in VSC is a lot more complex. So, we use eclipse since it is a lot more compatable with external libraries as a whole, including jUnit
