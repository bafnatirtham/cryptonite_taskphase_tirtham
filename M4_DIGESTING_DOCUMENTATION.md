# DIGESTING DOCUMENTATION
this module is about learning how to use/figure out all the programs.
The correct usage of programs depends in the proper specification of arguments to them.
It is like a set of rules for how to use the program

## 1. Learning from Documentation
In this challenge we have to use the argument of `--giveflag` in `/challenge/challenge` to get the flag

### Flag
`pwn.college{MD0hzjrv80N31Et7eMv2iw_Vysg.dRjM5QDL3kjM2czW}`

## 2. Learning Complex Usage
This challenge educates about how to use nested arguments to use program.
eg: ` file -name /path` uses two arguments one for file and the other for -name

Good to know: An esoteric programming language (or esolang) is a programming language designed to test the boundaries of computer programming language design
this command gave the flag `hacker@man~learning-complex-usage:/$ challenge/challenge --printfile /flag`

### Flag
`pwn.college{EMamnLbvsjuX2Nx2fFcwjroB6xc.dVjM5QDL3kjM2czW}`

## 3. Reading Manuals
In this challenge we learn about
1. the `man` command which is short for **"manual"**
2. it displays the manual of the command that u pass as an argument
3. Manpages are stored in a centralized database, which lives in the `/usr/share/man` directory
4. we can hit `q` to quit the manual

In this challenge we had to read the manual for "challenge" using `man challenge` and then press d for the description of the argument that will give us the flag
that argument was `--xxdazk NUM` where NUM =331
### Flag
`pwn.college{A_xADU3PxSdTZPBaEIz3Yk1tYxr.dRTM4QDL3kjM2czW}`

## 4. Searching Manuals
We can search manuals with / and press N or n to go to previous or next result respectively
we can also use ? instead of / to search backwards

In this challenge we have to use the information of (3) and (4) to find the flag.
After invoking `man challenge`, I used `/flag` to search for the flag and used **n** to go to the next result using wihc i got to know about the right argument `--uru`

### Flag
`pwn.college{gDLiwhgDZpVOhjsnmmCPnYG26hR.dVTM4QDL3kjM2czW}`

## 5. Searching for Manuals
This challenge involves a tricky version of using man i.e `man man` to find for manuals and then use existing pre learnt commands to find the hidden flag

Commands used to find the flag
`man man,
man -k challenge/challenge,
man ytcbldujbg,
/,
/challenge/challenge --ytcbld 462`

### Flag
`pwn.college{4YFy6t2cb9ldAuT-HjBbgTydtgz.dZTM4QDL3kjM2czW`

## 6. Helpful Programs


### Flag
` pwn.college{oyG3n0Pb7BehGvzcQyU0hgmZCaX.ddjM4QDL3kjM2czW}`













