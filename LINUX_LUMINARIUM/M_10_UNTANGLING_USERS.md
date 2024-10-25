# UNTANGLING USERS MODULE 10
There are a lot of users in the system rather than just hacker and root\
eg of a listed user: `root:x:0:0:root:/root:/bin/bash`\
Each line contains, separated by :'s; the username, an x as a placeholder for where the password used to be, the numerical user ID, the numerical default group ID, long-form user details, the home directory, and the default shell.

_Note: 'nobody' user is used to ensure that a program runs without any special privileges_

This module will cover upon various user maneuvers and learn the intended ways to switch users to administer the system.

## 1. Become root with su
In this challenge, we will learn about `su`\
1. `su` is a setuid binary.
2. This is not typically used to elevate to root access anymore, but it is an elegant utility.
3. Because it has the SUID bit set, su runs as root. Running as root, it can start a root shell.
4. Before allowing the user to elevate privileges to root, it checks to make sure that the user knows the root password (this is why it is obsolete/not in use anymore)

   In this challenge, we had to provide the given password to 'su' to retrieve the flag.
   ### Flag
   `pwn.college{Q8yO9IUZtARZJEixaXMdlT363Y0.dVTN0UDL3kjM2czW}`

## 2. Other users with su
We can give an argument to su to switch to another user instead of root.\
Syntax: `su [username]`

In this challenge, we had to switch to zardus user, provide the password and run /challenge/run to retrieve the flag

### Flag
`pwn.college{QkUauUcd6D1iitUqn2sjzcUsbsR.dZTN0UDL3kjM2czW}`

## 3. Cracking Passwords
When we enter a password for su, it compares it against the stored password for that user.\
These passwords used to be stored in /etc/passwd, but because /etc/passwd is a globally-readable file, this is not good for passwords\
Hence, these were moved to /etc/shadow.

Example:
```
sshd:*:19901:0:99999:7:::
zardus:$6$bEFkpM0w/6J0n979$47ksu/JE5QK6hSeB7mmuvJyY05wVypMhMMnEPTIddNUb5R9KXgNTYRTm75VOu1oRLGLbAql3ylkVa5ExuPov1.:19921:0:99999:7:::
```
1. Separated by `:`'s, the first field of each line is the username and the second is the password.
2. A value of * or ! functionally means that password login for the account is disabled
3. A blank field means that there is no password (a common misconception that allows password-less su), and
4. the long string such as Zardus `$6$bEFkpM0w/6J0n979$47ksu/JE5QK6hSeB7mmuvJyY05wVypMhMMnEPTIddNUb5R9KXgNTYRTm75VOu1oRLGLbAql3ylkVa5ExuPov1.` is the result of **_one-way-encrypting (hashing)_** Zardus' password from the last level (in this case, dont-hack-me)

5. When you input a password into su, it one-way-encrypts (hashes) it and compares the result against the stored value.
6. If the result matches, su grants you access to the user

If you have the hashed value of the password, you can crack it! Even though /etc/shadow is, by default, only readable by root, leaks can happen. This can be done using John The Ripper (a password cracking tool) (`john ./[process]`)

### Flag
`pwn.college{4ftY7IzzCdHyN-5jZlDfHKsN0kt.ddTN0UDL3kjM2czW}`

## 4. Using sudo
1. 'root' passwords are a pain to maintain, they can leak and they don't lend themselves well to larger environments (e.g., fleets of servers).
2. To address this `sudo` (superuser do) is used instead of `su`.
3. Unlike su, which defaults to launching a shell as a specified user, sudo defaults to running a command as root
4. Also unlike su, rather than authenticating via password, sudo relies on policies that it checks to determine the user's authorization run things as root.
   
   In this challenge, I used the command `sudo cat /flag` to access the flag as root user
   ### Flag
   `pwn.college{AzxXiuXcYVUcfmXmPrwCnly9gLW.dhTN0UDL3kjM2czW}`

# Summary

1. eg of a listed user: `root:x:0:0:root:/root:/bin/bash`
2. Each line contains, separated by :'s; the username, an x as a placeholder for where the password used to be, the numerical user ID, the numerical default group ID, long-form user details, the home directory, and the default shell.
3. 'nobody' user is used to ensure that a program runs without any special privileges
4. `su` is a setuid binary. Because it has the SUID bit set, su runs as root. Running as root, it can start a root shell.
5. We can give an argument to su to switch to another user instead of root.\
   Syntax: `su [username]`
6. When you input a password into su, it one-way-encrypts (hashes) it and compares the result against the stored value. If the result matches, su grants you access to the user
7. `john ./[process]` is used to crack the hashed password.
8. 'root' passwords are a pain to maintain, To address this `sudo` (superuser do) is used instead of `su`
9.  Unlike su, which defaults to launching a shell as a specified user, sudo defaults to running a command as root
10.  sudo relies on policies that it checks to determine the user's authorization run things as root.
