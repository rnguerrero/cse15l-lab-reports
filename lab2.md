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
      ArrayExamples.reversed(input1);
      assertArrayEquals(new int[]{0, 0, 0, 0, 0}, input1);
    
    }
    
    
The symptom of the failure inducing input is shown by the output after running jUnit:
 
![Both tests after running](https://github.com/rnguerrero/cse15l-lab-reports/blob/94bf2eca78b9b0103e982b97f76f1ca5f854ee3e/Lab3%20Pics/12341234.png)
  
  
