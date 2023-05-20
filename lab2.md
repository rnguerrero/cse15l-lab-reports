Lab Report 2 - Servers and Bugs - April 24, 2023
================================================
Intro
---

Hello! This is the 2nd lab report for CSE 15L, which covered primarily local servers and testing with jUnit

I don't know why, other than seeing how blockquote looks, but I felt possessed to put the following quote:

> Father. It's me, Michael. I did it. I found it. It was right where you said it would be. They were all there. They didn't recognize me at first but then they thought I was you. And I found her. I put her back together, just like you asked me to. She's free now. But something is wrong with me. I should be dead. But I'm not. I've been living in shadows. There is only one thing left for me to do now. I'm going to come find you... I'm going to come find you.

> -- William Afton

Other than that, I hope whoever is reading this has a good day :) 👍

---
Part 1 - StringServer Website
---

I created code that I have reasonable confidence in, but I am unable to run it, as when I launch it as a server,  the server itself functions as the NumberServer
we worked on during lab 2. I posted a problem about this on edstem, it is number #107. If this is still the only thing on here for part 1 upon submission, I have yet to 
figure out the issue I am having.

Edit: I figured how it works :) : I had to make the class name `Handler`. I suppose it has something to do with how URLHandler works. Since another java file used 
`Handler` as a class name in the repository, it used that file's server operations as opposed to `StringServer`'s


For this lab report's first assignment, I created a program called StringServer, that creates a local server. When the path reads `add-message`, the following query, 
which was labeled `s`, will be shown on the website. Additionally, for every additional string added using this path, the newly added string will appear on a new line, 
along every other string that I inputed using this method.

This is my code:

    >StringServer.java
    
    import java.io.IOException;
    import java.net.URI;

    class Handler implements URLHandler {
        String stringsOnSite = "";

        public String handleRequest(URI url) {
            if (url.getPath().equals("/")) {
                return stringsOnSite;
            } 
            else {
                if (url.getPath().contains("/add-message")) {
                    String[] parameters = url.getQuery().split("=");
                    if (parameters[0].equals("string")) {
                        return stringsOnSite += parameters[1] + "\n";
                    }
                }
                return "404 What the heck???";
            }
        }
    }

    class StringServer {
        public static void main(String[] args) throws IOException {
            if(args.length == 0){
                System.out.println("Must put port number, you fool");
                return;
            }

            int port = Integer.parseInt(args[0]);

            Server.start(port, new Handler());
        }
    }
    
When I start a port for this program, the terminal looks as follows:

![TerminalOfServerProgram](https://rnguerrero.github.io/cse15l-lab-reports/Lab3%20Pics/terminalServer.png)

The default page looks like this : 

![serverDefault](https://rnguerrero.github.io/cse15l-lab-reports/Lab3%20Pics/serverDefault.png)

Nothing appears, but the site is technichally showing an empty string, called `stringOnSite`. This is important for adding messages.

After making the path `/add-message?s=Hello` :

![serverDefault](https://rnguerrero.github.io/cse15l-lab-reports/Lab3%20Pics/serverHello.png)

The only method called `handleRequest`, where the input was the URL that I just entered. Within this method, it checks if the path is `add-message`. After doing so, it 
checks again if the first first element of the query is `s`. If both of these conditions are met, it adds the string that you inputed after the `=` followed by `/n` to
`stringsOnSite`, so
that the next string inputed using this path and query will be on a new line.
Finally, it returns `stringsOnSite`, so the page displays all prior messages along with the added message on a new line.

This can be seen after making the path `/add-message?s=How are you`

![serverDefault](https://rnguerrero.github.io/cse15l-lab-reports/Lab3%20Pics/serverHowAreYou.png)

Again, the `handleRequest` method is called, undergoing the same process as before, but instead adding `How are you` instead of `Hello` to `stringsOnSite`

It is important to note that if either the path does not contain `add-message` or if the query to the left of the `=` sign is exactly `s`, the message `404 What the heck???` will be displayed, so when using the program, you must make sure that 

---
Part 2 - Testing from Lab 3
---

Next, we were tasked with selecting a bug we observed with one of the methods in 

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
---

To cap off this lab report, I feel like I've learned a lot during these past two weeks. I suppose the most valuable thing I learned was about the nature of jUnit. I 
have heard of it, and continue to interact with it due to its prominence in CSE12, but we never got answers as to how it worked, leaving me with questions such as 'Why 
is it so different from checkExpect, which we used in cse 8B?', 'Why do we use eclipse for our programing assignments instead of VSC,' and 'Why are the PAs so 
differently formated?', but thanks to the recent lecture and labs, I now understand better the nature of jUnit as an external library, or a library that is not from a 
java library, so actually executing the tests in VSC is a lot more complex. So, we use eclipse since it is a lot more compatable with external libraries as a whole, 
including jUnit
