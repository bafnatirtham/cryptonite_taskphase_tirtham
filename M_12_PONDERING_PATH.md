# PONDERING PATH MODULE 12
This module will ponder upon the inbuilt commands such as `ls` and how does the shell find these programs.

## 1. The PATH Variable
1. There is a special shell variable, called PATH, that stores a bunch of directory paths in which the shell will search for programs corresponding to commands.
2. If we blankout the PATH using `PATH=""` it wouldnt be able to find the inbuilt commands and programs related to its functioning.
   
   In this challenge, I used the `rm` command first then set `PATH=""`. Now the rm command cannot be found and I used `/challenge/run` to get the flag which would otherwise be removed
   ### Flag
   `pwn.college{4AjmAYI9XXC-vFmKEIyPRIREEKv.dZzNwUDL3kjM2czW}`

## 2. Setting PATH 
1. PATH stores a list of directories to find commands
2. But for non standard commands we have to typically execute them by specifying the entire path.

   Example:
   ```
   hacker@dojo:~$ ls /home/hacker/scripts
   goodscript	badscript	okayscript
   hacker@dojo:~$ goodscript
   bash: goodscript: command not found
   hacker@dojo:~$ /home/hacker/scripts/goodscript
   YEAH! This is the best script!
   ```
3. If we want to launch useful scripts using their bare name, we need to add or replace directories in the PATH list.
   Example:
   ```
   hacker@dojo:~$ PATH=/home/hacker/scripts
   hacker@dojo:~$ goodscript
   YEAH! This is the best script!
   ```

   In this challenge, we had to overwrite PATH by `PATH="/challenge/more_commands"` and then execute `/challenge/run` to get the flag

   ### Flag
   `pwn.college{w1crpoGmDrj9vZlA33AvElqiHGE.dVzNyUDL3kjM2czW}`

## 3. Adding Commands
