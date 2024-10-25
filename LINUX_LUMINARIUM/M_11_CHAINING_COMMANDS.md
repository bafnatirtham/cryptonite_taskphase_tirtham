# CHAINING COMMANDS MODULE 11
This module will cover a few ways, aside from piping, that commands can be chained.

## 1. Chaining with Semicolons
1. The easiest way to chain commands is ;.
2. ';' separates commands in a similar way to how 'Enter' separates lines
(It is basically like ending statements. Once the terminal compiler encounters a ';' it considers the next line as the next command.

In this challenge we had to write two commands together using the semicolon(;). 
`/challenge/pwn ; /challenge/college` gave the flag.

### Flag
`pwn.college{EWFvDXFLh2RQt-Y4aiEUu-kncY3.dVTN4QDL3kjM2czW}`

## 2. Your First Shell Script
1. When we combine many commands with `;`, the length can be very long.\
2. Therefore, to avoid this we can create a shell script with a '.sh' suffix and then run it as a file.
3. We can execute by passing it as an argument to a new instance of our shell (bash).
4. When a shell is invoked like this, rather than taking commands from the user, it reads commands from the file.

In this challenge, I first created the shell script by `touch x.sh`, then  used `echo /challenge/pwn > x.sh` to store the first command and then used `echo /challenge/college >> x.sh` to append the second command into the x.sh shell script. Then I called `bash x.sh` to get the flag.

   ### Flag
   `pwn.college{AlU5JwNdJp3-A-OWvV9pSaaZDEl.dFzN4QDL3kjM2czW}`

## 3. Redirecting Script Output
For the shell, our shell script is just another command , which means that all the rules, formats and syntax for redirection can be used with the .sh files too\
In this challenge, we had to create a shell script, store our command and then pipe the output of the shell script into another command using piping '|'
```
touch x.sh
echo /challenge/pwn > x.sh
echo /challenge/college >> x.sh
bash x.sh | /challenge/solve
```
### Flag
`pwn.college{4bv5-jrQtig4cu66vka2Lm3LJ2J.dhTM5QDL3kjM2czW}`

## 4. Executable Shell Scripts
Instead of using bash again and again to call the shell script, we can in turn, make the shell script file executable using the file permissions

In this challenge we had to create a shell script to invoke a command and then change its file permission settings to read and then execute it using its relative path.
```
touch x.sh
echo /challenge/solve > x.sh
ls -l x.sh
-rw-r--r-- 1 hacker hacker 17 Oct 19 21:00 x.sh
chmod a+rwx x.sh
./x.sh
Congratulations on your shell script execution! 
```
### Flag
`pwn.college{Q1w_dPhxSCkytmO5B0Ct1m13Nt5.dRzNyUDL3kjM2czW}`

# Summary
1. The easiest way to chain commands is ;. ';' separates commands in a similar way to how 'Enter' separates lines (It is basically like ending statements)
2. When we combine many commands with `;`, the length can be very long. Therefore, to avoid this we can create a shell script with a '.sh' suffix and then run it as a file.
3. We can execute by passing it as an argument to a new instance of our shell (bash).
4. **_NOTE_**: Use > to write the command and >> to append and add to the command otherwise the commands in the .sh file get replaced
5. Instead of using bash again and again to call the shell script, we can in turn, make the shell script file executable using the file permissions, using `chmod` and then directly executing `./x.sh` (relative path)



