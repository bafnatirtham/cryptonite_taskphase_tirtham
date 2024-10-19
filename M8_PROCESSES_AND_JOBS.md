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

## 6. Backgrounding Processes
The `fg` command is used to resume processes in the foreground\
The `bg` command is used to resume processes in the background. This will allow the process to keep running, while giving you your shell back to invoke more commands in the meantime.

We can also check the difference between suspended and background properties by enabling "stat" column using `ps -o user,pid,stat,cmd`
1. T stands for suspended
2. S stands for sleep (waiting for input)
3. R stand for actively running
4. + means process is in the foreground

     In this challenge, we had to launch /challenge/run, suspend it, put it in the background using 'bg' and then launch /challenge/run again to get the flag

     ### Flag
     `pwn.college{4tK7ikAH9t3tMNNU-dUX7qi1v7y.ddDN4QDL3kjM2czW}`

## 7. Foregrounding Processes
Using `fg` we can also foreground a backgrounded process

### Flag
`pwn.college{o68fHSXkfU8_ub-kBE8MRZX3lWL.dhDN4QDL3kjM2czW}`

## 8. Starting Backgrounding Processes
We can put a command directly into the background without 'suspending' (Ctrl+Z) it first and then using 'bg'.\
For this, we have to append "&" to the command we are entering\
eg: `/challenge/run &` will directly start the process in the background.

### Flag
`pwn.college{8miaNvTYblEIlZE3M6694egTNa_.dlDN4QDL3kjM2czW}`

## 9. Process Exit Codes
1. Every shell command, including every program and every builtin, exits with an exit code when it finishes running and terminates, This can be used by the shell, or the user of the shell to check if the process succeeded in its functionality.
2. You can access the exit code of the most recently-terminated command using the special ? variable. We need to prepend it with $ to read its value.
3. commands that succeed typically return 0, commands that fail typically return a non-zero value, most commonly 1; sometimes an error code identifies a specific failure mode.

   ### Flag
   `pwn.college{o4n3_hc5lnL_41KDNqY_Tp6FAlN.dljN4UDL3kjM2czW}`


