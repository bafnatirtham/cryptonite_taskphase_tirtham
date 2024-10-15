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

   ## 5. Redirecting Input
   The `<` character is used to redirect the standard input to programs.\
   In this challenge, we used `echo`,`<`and `>` collectively to redirect the flag

   ### Flag
   `pwn.college{8KP-4ONKMs-9_obanp4RJlB0BpE.dBzN1QDL3kjM2czW}`

   ## 6. Grepping Stored Results
   Here we used concept of grepping(searching) and io/op i.e < and > to find the flag

   ### Flag
   `pwn.college{8BOdTtfUnT4AmxuA4JEF4f2pNxQ.dhTM4QDL3kjM2czW}`

   ## 7. Grepping Live Output
   1. `|` is the pipe operator
   2. We can avoid the need to store the results in a file by piping
   3. Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the             command to the right of the pipe/
       `/challenge/run | grep pwn.college`
      
      ### Flag
      `pwn.college{8xrmk-Kt_iW8BH_prRbPpZy3bC8.dlTM4QDL3kjM2czW}`

   ## 8. Grepping Errors
   1. The | operator redirects only standard output to another program. There is no 2| form of the operator
   2. For this, `>&` operator redirects a file descriptor to another file descriptor.
   3. We can have a two-step process to grep through errors: first, we redirect standard error to standard output (2 >& 1) and then pipe the now-combined stderr and stdout as normal (|)
  
      `/challenge/run 2>&1 | grep pwn.college`

      ### Flag
      `pwn.college{wOMvDghtq4eBIlMVromOLnmDYUf.dVDM5QDL3kjM2czW}`

   ## 9. Duplicating piped data with tee
   The tee command, named after a "T-splitter" from plumbing pipes, duplicates data flowing through your pipes to any number of files provided on the command line

   Code:/
   ```\
   /challenge/pwn | tee pwnop | /challenge/college
   /challenge/pwn --secret 4-WvrsrV | /challenge/college
   ```

   ### Flag
   `pwn.college{4-WvrsrVaQEmJxhqn2VDVGTJ_zv.dFjM5QDL3kjM2czW}`
   
      
   
   
