# PONDERING PATH MODULE 12
This module will ponder upon the inbuilt commands such as `ls` and how does the shell find these programs.

## 1. The PATH Variable
1. There is a special shell variable, called PATH, that stores a bunch of directory paths in which the shell will search for programs corresponding to commands.
2. If we blankout the PATH using E it wouldnt be able to find the inbuilt commands and programs related to its functioning.
   In this challenge, I used the `rm` command first then set `PATH=""`. Now the rm command cannot be found and I used `/challenge/run` to get the flag which would otherwise be removed
   ### Flag
   `pwn.college{4AjmAYI9XXC-vFmKEIyPRIREEKv.dZzNwUDL3kjM2czW}`
