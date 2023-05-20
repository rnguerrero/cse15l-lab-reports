Lab 4 - Vim interfacing 
===

For this weeks lab report, I will be recording my exact keyboard inputs to complete a set of tasks from this week's lab.

For clarity, everything that I type in the terminal will be in inline code, and everything enclosed by a `<>` is a specific key / command done with one keyboard input

1 . Log into ieng6
---

In the terminal, I did the following inputs consecutively: `ssh cs15lsp23fx@ucsd.edu <enter>`, and then I entered my password, which I will not write out for this lab, and then I pressed `<enter>`

![Step1Image]()

2 . Clone your fork of the repository from your Github account
---
In the terminal, I typed out `git clone https://github.com/rnguerrero/lab7.git`, which is my fork of this labs files.
I then typed `cd lab7` so that my active directory would be changed to lab7. 

![Step2Image]()

3 . Run the tests, demonstrating that they fail
---
Within the lab7 repository, there is a bash file called test.sh which runs the java files that run according jUnit tests. So, I only have to type `bash test.ssh <enter>`

![Step3Image]()


4 . Edit the code file to fix the failing test
---
Here, we will use vim to change the java file ListExamples.java so that there are no errors. To do so, I press the following keys: `vim ListE <Tab> .java <enter>` Here, I pressed tab in an attempt to auto complete the file name, but since I ran the java file, there was also a .class file, so I had to manually type .j and <tab> to ensure that I got to the right file. I then press 

![Step4Image]()

5 . Run the tests, demonstrating that they now succeed
---

![Step5Image]()

6 . Commit and push the resulting change to your Github account
---

