Lab Report 3 - 
=======
May 10, 2023
---

In the past couple of weeks, we learned a lot about command line arguments, and different command's use cases and what they can do.

In this lab report, I will be covering the use of the `grep` command, and the applications of some if its options

1 - The base `grep` command
---
On its own, the grep command has a simple use. Its function is to print all the lines of the selected files that match a given string to the command line. For example, in order to search for "outbreaks" in the file biomed/1471-2458-3-11.txt from technical, I ran the following line of code in the command line :

`$ grep "outbreaks" biomed/1471-2458-3-11.txt`

And got the following output :

`        
         based on studies undertaken during outbreaks of the

        observed in outbreak settings. Large outbreaks have been
        
        outbreaks of cryptosporidiosis in which the vehicle of
        
        outbreaks due to cryptosporidiosis have implicated food
        
        Person-to-person outbreaks have been better documented,
        
        persons is relevant since most major known outbreaks of
`

Another command that I using just grep was :

`$ grep "fire" government/Media/Fire_Victims_Sue.txt`

Which produces the output :

`Nine families displaced by a fire at Alamo Hills Apartments in`

For the most part, the base grep command is simple best used for expectedly low outputs. It is useful for simply visualizing every line in a file the contains a pattern you are searching for. Otherwise, you may get overwhelmed with the amount of produced lines from a file, which will end up being useless for most applications. This is where options can make grep a lot more useful.

The -i option
---

Lets take the command `$ grep "neurological" biomed/1472-684X-1-5.txt` as an example. The output would be :

`The neurological changes associated with the dying`

However, if we changed the command to `$ grep "Neurological" biomed/1472-684X-1-5.txt`, where we only change the case of the first letter, we will get the output : 

`Neurological Changes`

Because of the change in case, our output will change. However, we can use the -i option to ignore the case of the string. With the mentioned example, it would look like this: 

`          Neurological Changes
          
          The neurological changes associated with the dying
`

As seen, it gives the cumulative output of the two cases, with the output contains both an uppercase and a lowercase variation of the inputted string.

Another example of -i in use is with the command `$ grep -i "The most" biomed/1472-684X-1-5.txt`

`          issue in turn. The following addresses some of the most

          responsive to treatment it may be [ 34 ] . The most
          
          Breathlessness may be one of the most distressing
          
          Dopamine-mediated nausea is probably the most
          
          Fatigue/weakness is the most frequent distressing
          
          alarming if it is not understood. The most common are
`

In general, the -i option is useful for finding all lines with a specific string without discriminating against the case of the letter. This is especially useful for searching for words or phrases that may regularly start with both uppercase and lowercase letters, such as things that the words "the" or "a".

The -c option
---



The -r option
--
