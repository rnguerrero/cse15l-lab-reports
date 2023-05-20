Lab 4 - Vim interfacing 
===

For this weeks lab report, I will be recording my exact keyboard inputs to complete a set of tasks from this week's lab.

For clarity, everything that I type in the terminal will be in inline code, and everything enclosed by a `<>` is a specific key / command done with one keyboard input

1 . Log into ieng6
---

In the terminal, I did the following inputs consecutively: `ssh cs15lsp23fx@ucsd.edu <enter>`, and then I entered my password, which I will not write out for this lab, and then I pressed `<enter>`

![Step1Image](https://github.com/rnguerrero/cse15l-lab-reports/blob/main/LabReport%204%20pictures/ieng6Login.png)

2 . Clone your fork of the repository from your Github account
---
In the terminal, I typed out `git clone https://github.com/rnguerrero/lab7.git`, which is my fork of this labs files.
I then typed `cd lab7` so that my active directory would be changed to lab7. 

![Step2Image](https://github.com/rnguerrero/cse15l-lab-reports/blob/main/LabReport%204%20pictures/cloningLab7.png)

3 . Run the tests, demonstrating that they fail
---
Within the lab7 repository, there is a bash file called test.sh which runs the java files that run according jUnit tests. So, I only have to type `bash test.ssh <enter>`

![Step3Image](https://github.com/rnguerrero/cse15l-lab-reports/blob/main/LabReport%204%20pictures/testsFail.png)

4 . Edit the code file to fix the failing test
---
Here, we will use vim to change the java file ListExamples.java so that there are no errors. To do so, I press the following keys: `vim ListE <Tab> .java <enter>` Here, I pressed tab in an attempt to auto complete the file name, but since I ran the java file, there was also a .class file, so I had to manually type .j and tab to ensure that I got to the right file.
I then press `:44 <enter>`, which brings me to the line in the file that has the bug. I then press `e x i 2`. What this does is move to the end of the current word, which happens to be the variable that is causing the bugs, removes the character that the cursor is currently on, enters insert mode, and inserts the character 2, which will fix the bugs. Finally, I press `<esc> :wq`, which allows me to enter normal mode and save the changes I made.

![Step4Image](https://github.com/rnguerrero/cse15l-lab-reports/blob/main/LabReport%204%20pictures/madeChanges.png)

5 . Run the tests, demonstrating that they now succeed 
---
At this step, I simply press the keys `<up> <up> <enter>` since I had run the test.sh file before the vim command. It shows now that the tests passed.

![Step5Image](https://github.com/rnguerrero/cse15l-lab-reports/blob/main/LabReport%204%20pictures/testsPass.png)

6 . Commit and push the resulting change to your Github account
---
Finally, to commit the file, I typed `git add ListE <tab> .j <tab> <enter>`, which lets git know that when I commit, I only want to make changes to ListExamples.java. Afterwards, I typed `git commit`, which launched vim, prompting me for a commit message. For this message, I chose to type `fixed ListExamples.java bugs`, and I finally typed `<esc> :wq <enter>` to actually commit the changes.

![Step6Image](https://github.com/rnguerrero/cse15l-lab-reports/blob/main/LabReport%204%20pictures/commitedChangesMessage.png)
  
Finally, we are done. These are all of the consecutive inputs I needed to do to accomplish this task : 
`ssh cs15lsp23fx@ucsd.edu <enter> [Typed password] <enter> git clone https://github.com/rnguerrero/lab7.git cd lab7 bash test.ssh <enter> vim ListE <Tab> .java <enter> :44 <enter> e x i 2 <esc> :wq <up> <up> <enter> git add ListE <tab> .j <tab> <enter> git commit fixed ListExamples.java bugs <esc> :wq <enter>`

  
  
  
  

