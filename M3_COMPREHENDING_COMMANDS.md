# COMPREHENDING COMMANDS MODULE 3
This module is about learning more basic Linux Commands

## 1. cat: not the pet, but the command!
1. The `cat` command is used to read out files
2. `cat` will con**cat**enate multiple files if provided multiple arguments.
3. if `cat` does not have any arguments, it will read from the terminal input and output it.

In this challenge, we had to read _flag_ file which was in _home_ directory, we did this using `cat flag`

### Flag
`pwn.college{AVckOyPFi4Ru4tO00lz_VOkUou7.dFzN1QDL3kjM2czW}`

## 2. catting absolute paths
Two takeaways from this challenge
1. Arguments of `cat` can be specifed as absolute paths also.
2. `/flag` is where the flag always lives in pwn.college

In the challenge the flag was located inside `/flag` so we can directly just type the ocmmand `cat /flag` to get the flag.

### Flag
`pwn.college{oXf_kFvoSgcfTjG8f9eB5NEAsUq.dlTM5QDL3kjM2czW}`

## 3. more catting practice
involved using `cat` with absolute paths without using `cd`.

### Flag
`pwn.college{cFbOR4hjCl68dr5A390eFqzns39.dBjM5QDL3kjM2czW}

## 4. grepping for a needle in a haystack
this challenge teaches about the `grep` command which can search for a particular string inside a large data file.
i used `grep pwn.college /challenge/data.txt` to find the flag; here _pwn.college_ is the string to be searched and _/challenge/data.txt/_ is the absolute path of the file in which we want to search.

### Flag
`pwn.college{kYwGDA7MBVNzm--w8KWSMyFbQcA.ddTM4QDL3kjM2czW}`

## 5. Listing Files
1. `ls` command stands for **"listing files"**
2. ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided

In this challenge we had to list the files in `/challenge` directory to find the renamed run folder and retrieve the flag

### Flag
`pwn.college{EbSsneeW0XkHiELGybto5eN_WNc.dhjM4QDL3kjM2czW}`

## 6. Touching Files
the `touch` command allows us to create new blank files by _touching_ it.

In this challenge, we had to use the `touch` command to create two new files and then run `/challenge/run` to get the file

### Flag
`pwn.college{0beTPxAGvCzk5IAd3LZf8b3o2yy.dBzM4QDL3kjM2czW}`

## 7. Deleting Files
the `rm` (remove) command is used to delete any unnecessary files from the directory
In this challenge, we had to delete a file using the `rm` command and then run `/challenge/check` to get the flag

### Flag
`pwn.college{wixZj3K1CAcnaoPouQeudaVYj6f.dZTOwUDL3kjM2czW}`

## 8. Hidden Files
1. `ls` doesn't list all the files by default.
2. Linux does not show files that start with a '.'
3. To view these files we have to use `ls -a` command

   In this challenge we had to use `ls -a` in the `/` directory. After finding the hidden flag file, i tried to use cd first but it was not working, Then i used `cat ./.flag-2884617699495` to access the flag

### Flag
`pwn.college{QbOYWIR4dswLBT-HFX-7qk_5-pU.dBTN4QDL3kjM2czW}`

## 9. An Epic Filesystem Quest
here we have to use the commands `cd`, `ls` and `cat` to find the hidden clues and eventually the flag.
one take away form this challenge was that: when we can't use `cd`, we can use `ls` and `cat` to read the files .

### Flag
`pwn.college{MGemnrg31p0V8dfn9q2OM78_4-8.dljM4QDL3kjM2czW}`



    

