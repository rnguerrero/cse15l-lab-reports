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
        
        based on studies undertaken during outbreaks of the
        observed in outbreak settings. Large outbreaks have been       
        outbreaks of cryptosporidiosis in which the vehicle of     
        outbreaks due to cryptosporidiosis have implicated food        
        Person-to-person outbreaks have been better documented,        
        persons is relevant since most major known outbreaks of

Another command that I using just grep was :

`$ grep "fire" government/Media/Fire_Victims_Sue.txt`

Which produces the output :

`Nine families displaced by a fire at Alamo Hills Apartments in`

For the most part, the base grep command is simple best used for expectedly low outputs. It is useful for simply visualizing every line in a file the contains a pattern you are searching for. Otherwise, you may get overwhelmed with the amount of produced lines from a file, which will end up being useless for most applications. This is where options can make grep a lot more useful.

The -i option
---

Lets take the command `$ grep "neurological" biomed/1472-684X-1-5.txt` as an example. The output would be :

         The neurological changes associated with the dying

However, if we changed the command to `$ grep "Neurological" biomed/1472-684X-1-5.txt`, where we only change the case of the first letter, we will get the output : 

         Neurological Changes

Because of the change in case, our output will change. However, we can use the -i option to ignore the case of the string. With the mentioned example, it would look like this: 

         Neurological Changes
          
         The neurological changes associated with the dying


As seen, it gives the cumulative output of the two cases, with the output contains both an uppercase and a lowercase variation of the inputted string.

Another example of -i in use is with the command `$ grep -i "The most" biomed/1472-684X-1-5.txt`

          issue in turn. The following addresses some of the most
          responsive to treatment it may be [ 34 ] . The most          
          Breathlessness may be one of the most distressing          
          Dopamine-mediated nausea is probably the most          
          Fatigue/weakness is the most frequent distressing          
          alarming if it is not understood. The most common are


In general, the -i option is useful for finding all lines with a specific string without discriminating against the case of the letter. This is especially useful for searching for words or phrases that may regularly start with both uppercase and lowercase letters, such as things that the words "the" or "a".

The -c option
---

Lets use the following grep command, `$ grep "the" biomed/ar624.txt` 

The first few lines of output would be : 

        Autoreactive T cells are primarily eliminated in the
        the autoreactive T cells, however, may escape from negative
        selection and are released into the periphery. These
        self-reactive T cells are exquisitely regulated, and their
        demonstrated the existence of regulatory T-cell subsets
        CD25 (the α-chain of IL-2 receptor) [ 4 5 ] . Functional
        stimulation, but inhibit the activation of conventional
        of the CD4 +CD25 +T cells depends on signaling via the
        B7/CD28 costimulation is essential for the development and
        ...
         
After this, there are over a hundred more lines, all containing the word "the"
  
If our intention was to count the amount of lines that contain the word "The", it would be pretty laborous to count each line one by one. However, with the help of the `-c` option, we can make this task a lot easier. Implementing the `-c` option, we can run the command `$ grep -c "the" biomed/ar624.txt`, which yeilds the following output:

         125
         
This can also be used in conjunction with the `-i` option, which is manifested in the command `$ grep -c -i "the" biomed/ar624.txt`, which yields the following output:

         147
         
With the `-c` option, we can make counting the amount of lines that contain a certain pattern a lot easier than with the base `grep` command. 

The -r option
--
Now lets say that we want to search for the term "Nitro" in all of the files in `technical/biomed`. This would be simple, just type in the path for every text file in `technical/biomed`, if not for the fact that this directory has hundreds of text files. Naturally, typing in each and every path would be far to laborous. One way to prevent this from happening is by using the `-r` option.

For the task listed above, our command would look like `$ grep -r "Nitro" biomed/`, and yields the output : 

         biomed/1471-2091-3-4.txt:          Pharmacia Biotech. Nitrocefin was purchased from Becton
         biomed/1471-2091-4-5.txt:          or N-p-Tosyl-Gly-Pro-Lys-p-Nitroanilide (final
         biomed/1471-2172-2-3.txt:          by SDS-PAGE, transferred to Nitrocellulose and probed
         biomed/1471-2180-1-16.txt:          electrophoretically to Nitrocellulose paper (0.45 μm
         biomed/1471-2180-2-22.txt:          bath at 160 watts) for 1 h at room temperature. Nitrogen
         biomed/1471-2210-1-10.txt:          nitrocellulose membranes (NitroBind, MSI, Westborough,
         biomed/1471-2253-2-5.txt:          Nitrous oxide
         biomed/1471-2407-1-15.txt:          Nitrocellulose membranes were then incubated with the
         biomed/1477-7827-1-31.txt:          MA) and actin (Sigma). Nitrocellulose membranes (Hybond
         biomed/ar407.txt:          Nitrocellulose membranes were blocked with 5% nonfat milk
         biomed/bcr631.txt:          Chemical Company. Sephadex G-50 was from Pharmacia. Nitro
         biomed/cc4.txt:          ppm (CFPO, Air Liquide, France). Nitrogen oxides (NOX)
         
I did it again, but this time in conjunction with the `-i` and `-c` option, to count that amount of times "Nitro" appears regardless of case"

We would first do the command `$ grep -i -r "Nitro" biomed/ > NitroCount.txt`, which compiles all of the lines the contain "Nitro" regardless of case into a file. Then, we would run `$ grep -i -c "Nitro" NitroCount.txt`, which essentially counts the amount of lines in NitroCount.txt which would be the total amount of times Nitro appears in all of `technical/biomed/`, which yields the output :

         370

The `-r` option is very useful, as it allows for the use of `grep` over the span of many different files at the same time. It also comes with the added utility of telling the user which file each line is from.

Conclusion
---

All-in-all, the `grep` command is only so powerful on its own, but in conjunction with specific options and combinations of options, such as `-i`. `-c`, and `-r`, only dramatically improve the utility of the `grep` command. 

All options were found on [this](https://geekflare.com/grep-command-examples/#:~:text=16%20grep%20Command%20Examples%20to%20Help%20You%20in,...%208%20Limit%20grep%20Output%20...%20More%20items)	this website
