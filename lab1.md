Lab Report 1
=
April 10th, 2023 
-

Hello all of you 15L students (probably just me), this is going to be a guide on how to log into a course-specific account on `ieng6`.

**1) Installing Visual Studio Code**
This step is easy enough. If you're working on your main computing device, the one you have been using for previous CS classes up until now, this should already be done. However, if you do not have VSCode download for any reason, such as you are working on a different device, please do download the code editor here :

[VSCode Download](https://code.visualstudio.com/download)

After everything is downloaded, you should be able to open VSC. It should look something like this :

![VSC Home Screen](https://rnguerrero.github.io/cse15l-lab-reports/VSCode%20Downloaded.png)

Another thing to be downloaded is Git for windows. If you haven't already download it here:

[Git Download](https://gitforwindows.org/)

After all this, we're ready for the next step

**2) Remotely Connecting to ieng6**

Next, open a terminal on VSC. On the top right of the terminal, there is a `+` sign, with a dropdown option. You have to click on the dropdown that reads `Git Bash (Default)`.

Then, use `ssh` in  the bash terminal. It will like this, (This one is mine, if attempting to access another student account, replace the `fx` with the two letters corresponding to your account).

`$ ssh cs15lsp23fx@ieng6.ucsd.edu`

After pressing enter, a new line will be presented. It looks like this:

`(cs15lsp23fx@ieng6.ucsd.edu) Password:`

Here, you must blindly type in the password that corresponds to that account. (You will see below that I didn't take to this well with the amount of failed password attempts)

After succsesfully doing so, you will see something like this:

![GettingLoggedIn](https://rnguerrero.github.io/cse15l-lab-reports/GettingLoggedIn.png)

If you do, then congratulations! You logged into your account on `ieng6`

**3) Trying Out Some Commands**

Now, you are free to play around in the terminal and see what there is to do!

General guide of commands from this week's notes:

- `cat <path>` : Prints the content of one or more files. 
  
- `ls <path>` : Lists out all files / folders in the path.
  
- `pwd` : Prints the current working directory, or where you are currently working.
  
- `cd <path>` : Changes the current working directory, or where you are currently working.

Below are some implementations of the above commands. Feel free to expand further on what is seen:

![Trying Out Commands](https://rnguerrero.github.io/cse15l-lab-reports/ExperimentingWithieng6.png)
why not working????
