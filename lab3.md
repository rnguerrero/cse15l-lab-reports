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

`        based on studies undertaken during outbreaks of the

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

For the most part, the base grep command is simple best used for expectedly low outputs. Otherwise, you may get overwhelmed with the amount of produced lines from a file, which will end up being useless for most applications. This is where options can make grep a lot more useful.
