# PROCESSES AND JOBS MODULE 8
1. Computers execute software to get stuff done. 
2. In modern computing, this software is split into two categories: _operating system kernels_ and _processes_
3. eg: When Linux starts up, it launches an init (short for initializer) process that, in turn, launches a bunch of other processes which launch more processes until, eventually, ythe command line shell is launched, which is also a process.

## 1. Listing Processes
   1. The `ps` command is used to list running processes in the terminal
   2. Each process has a _numerical identifier_ (the Process ID, or PID), which is a number that uniquely identifies every running process in a Linux environment. We also see the _terminal on which the commands are running_, and the total amount of _cpu time_ that the process has eaten up so far 
   3. There are two ways to specify arguments in 'ps':
       1. "Standard" Syntax: in this syntax, you can use:
           1. `-e` to list "every" process and
           2. `-f` for a "full format" output, including arguments.
          These can be combined into a single argument `-ef`.

       2. "BSD" Syntax: in this syntax, you can use:
           1. `a` to list processes for all users
           2. `x` to list processes that aren't running in a terminal, and
           3. `u` for a "user-readable" output.
          These can be combined into a single argument `aux`.

   4.  `ps -ef` and `ps aux` result in slightly different, but cross-recognizable output.

### Flag
  `pwn.college{UvcGaoguoV18_1UG8Ub2v3-Ozaj.dhzM4QDL3kjM2czW}`
  
## 2. Killing Processes
  1. `kill` command is used to terminate a process in a way that gives it a chance to get its affairs in order before ceasing to exist.
  2. We need to enter the "process id" into the kill command to kill the process.

     Using this  information, I got the flag as:
     ### Flag
     `pwn.college{A7B48OgefWEnjiWCFvJZBIV4kuB.dJDN4QDL3kjM2czW}`

## 3. Interrupting Processes
We can use **Ctrl+C** to  send an _"interrupt"_ to whatever application is waiting on input from the terminal and causes the application to cleanly exit.

  ### Flag
  `pwn.college{w6InMirO37lD2huARDfnD4IAgxY.dNDN4QDL3kjM2czW}`

## 4. Suspending Processes
We can use **Ctrl+Z** to _"suspend"_ processes into the background

### Flag
`pwn.college{AUrB4i7KxM5FPfI8pO5ne0sFl14.dVDN4QDL3kjM2czW}`

## 5. Resuming Processes
We can use the `fg` command to resume the suspended processes and put it back in the foreground of your terminal.

### Flag
`pwn.college{UERrJ6bu7yNCiyPlVmGk50SSCS7.dZDN4QDL3kjM2czW}`
