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

