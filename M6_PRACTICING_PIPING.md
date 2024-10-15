# PRACTICNG PIPING MODULE 6
This module will give us an overview on input and output redirection.
Every process in Linux has three initial, standard channels of communication:
1. `stdin` or Standard Input is the channel through which the process takes input
2. `stdout` or Standard Output is the channel through which processes output normal data
3. `stderr` or Standard Error is the channel through which processes output error details

   ## 1. Redirecting Output
   The `>` character is used to redirect the standard output to files.
   
   eg: `echo PWN > COLLEGE` will store the word 'PWN' to the file COLLEGE

   ### Flag
   `pwn.college{MoGDSFFZjYoGAi3s3m5aVXozmEU.dRjN1QDL3kjM2czW}`

   ## 2. Redirecting More Output
   This challenge teaches us that other than echo we can also redirect the output of any command.
   
   I used `/challenge/run > myflag` to redirect the output to file 'myflag' and then used cat command to get the flag

   ### Flag
   `pwn.college{EXWedicIkGTQ1reSFeQbyLCYRf5.dVjN1QDL3kjM2czW}`

   ## 3. Appending Output
   If we want to append the output of several commands in one file instead of creating new files everytime, we can use `>>`

   1. **>>** : append mode
   2. **>** : truncation mode

      I used the append mode to redirect output --> `/challenge/run >> /home/hacker/the-flag` and then cat it to get the flag

      ### Flag
      `pwn.college{ADbJA8z3eGFJXuKipJ-XYtl8biA.ddDM5QDL3kjM2czW}`

   ## 4. Redirecting Errors
   A File Descriptor (FD) is a number the describes a communication channel in Linux.  eg:\
    FD 0: Standard Input\
    FD 1: Standard Output\
    FD 2: Standard Error\
  When you redirect process communication, you do it by FD number, though some FD numbers are implicit. For example\
   a > without a number implies 1>, which redirects FD 1 (Standard Output),
   simiilary 2> will redirect errors and so on.

   ### Flag
   ` pwn.college{cV2cmLqRFTYK1pqt94HSV70ydU2.ddjN1QDL3kjM2czW}`
   
