# PERCEIVING PERMISSION MODULE 9
This module will teach us about permissions/file modes of a file.\
We can access the permissions of a file/directory using `ls -l`.\

**Example of permissions:**
```
-rw-r--r-- 1 hacker hacker    0 May 22 13:42 college_file
drwxr-xr-x 2 hacker hacker 4096 May 22 13:42 pwn_directory
```

1. The File Type\
   The first character of each line represents the file type
   1. The 'd' indicates it is a _file directory_
   2. The '-' indicates it is a _file_

2. The Permissions\
   The next nine characters are the actual permissions of the file, further divided into 3-3-3.
   1. The first three characters denote the permissions that the _user who owns the file ("owner")_ has to the file.
   2. The next three characters denote the permissions that the _group who owns the file ("group")_ has to the file.
   3. The last three characters denote the permissions that _all other access (other users and other groups)_ has to the file.

3. Ownership Information\
   There are two columns: one that shows the user who owns the file and the other shows the group who owns the file.


## 1. Changing File Ownership
  1. Every file in Linux is owned by a user on the system\
  2. The two most important user accounts are:
     1.  The user account
     2.  `root`: This is the administrative account. Taking over the root user means we have almost certainly achieved our hacking objective!
  
  4. The **change ownership** command `chown` is used to change the ownership of files i.e `chown [username] [file]`.\
     Typically, `chown` can only be invoked by the root user.
     
Using all this information, we retrieved the flag: 
  ### Flag
  `pwn.college{IKgDfRyxgRVz47O3-2O7aA6fWoM.dFTM2QDL3kjM2czW}`

## 2. Groups and Files
1. The `id` command is used to check what groups we are in.
2. Files have both an owning _user_ and _group_. A group can have multiple users in it, and a user can be a member of multiple groups.
3. The most common use-case for groups is to control access to different system resources.
4. Group ownership can be changed with the `chgrp` (change group) command.

   ### Flag
   `pwn.college{A6-L0i3YXi4Zxg958ZN8twkKc1U.dFzNyUDL3kjM2czW}`

## 3. Fun with Groups Names
There is a convention in Linux that every user has their own group, but this does not have to be the case. 

In this challenge, the user was in a random group. We had to figure out this group and then use `chgrp` to retrieve the flag

### Flag
`pwn.college{4XX1icF7ufh-dr38wZZNp92oknP.dJzNyUDL3kjM2czW}`

## 4. Changing Permissions
In the 10 character encoding of the permission,\
the very first character stands for the file type;\
the next three stand for the owning user, the next three for the owning group, and the last three for other access.

Each character represent permission for a different type:
1. `r` - user/group/other can read the file (or list the directory)
2. `w` - user/group/other can modify the files (or create/delete files in the directory)
3. `x` - user/group/other can execute the file as a program (or can enter the directory, e.g., using `cd`)
4. `-` - nothing (or _cannot execute_)

The `chmod` command is used to ***change the file permissions***\
Syntax: `chmod [OPTIONS] MODE FILE *`\
MODE can be specified in two ways: 
1. as a modification of the existing permissions mode, or
2. as a completely new mode to overwrite the old one.

**Modifying an existing mode:**
`chmod` allows you to tweak permissions with the mode format of `WHO+/-WHAT`
1. WHO is:
   1. user(u)
   2. group(g)
   3. other(o)
      
2. WHAT is:
   1. read(r)
   2. write(w)
   3. execute(x)
      
3. (a) stands for all the modes, (+) stands for adding permissions, (-) stands for removing permissions\
   eg: `a-rwx` removes all permissions for the user, group, and world

   Using all this information, I changed the permissions of the /flag file to `a+rwx *` and then catted the /flag file to read the flag.

   ### Flag
   `pwn.college{Q5Cg_UviAg8f-wj2ISotF4sN8jA.dNzNyUDL3kjM2czW}`

## 5. Executable Files
In this challenhge we had to use all the previous information, to change the execution permissions and retrieve the flag i.e. \
```
chmod a+rwx /challenge/run
/challenge/run
```
### Flag
`pwn.college{UYvjiDN_GROyR-r8d3vnxZNhYuS.dJTM2QDL3kjM2czW}`

## 6. Permission Tweaking Practice
In this challenge, we had to use all the current knowledge of permissions and tweak it 8 times to get the flag
### Flag
`pwn.college{8vQ0vlbiWTmaDy2wRHMgZRbwNRj.dBTM2QDL3kjM2czW}`

## 7. Permission Setting Practice
In addition to adding and removing permissions, `chmod` can also simply set permissions altogether, overwriting the old ones. This is done by using = instead of - or +.\
1. `chmod a=rwx` sets read, write, and executable permissions for the user, group, and world
2. `chmod u=rw,g=r /challenge/pwn` will set the user permissions to read and write, and the group permissions to read-only
3. `chmod u=rw,g=r,o=- /challenge/pwn` will set the user permissions to read and write, the group permissions to read-only, and the world permissions to nothing at all\
   **We can zero out permissions with '-'**

   ### Flag
   `pwn.college{AIFmN8nHyP8dwHYc64BqeXRdYE3.dNTM5QDL3kjM2czW}`

## 8. SUID
There are many cases in which non-root users need elevated access to do certain system tasks. The system admin can't be there to give them the password every time a user wanted to do a task that only root/sudoers can do.\
For this purpose, The **"Set User ID" (SUID)** permissions bit _allows the user to run a program as the owner of that program's file._\
eg:
```
ls -l /usr/bin/sudo
-rwsr-xr-x 1 root root 232416 Dec 1 11:45 /usr/bin/sudo
```
The s part in place of the executable bit means that the program is executable with SUID. It means that, regardless of what user runs the program (as long as they have executable permissions), the program will execute as the owner user.\
`chmod u+s [program]` is used to set a file's SUID bit

_Note: Giving the SUID bit to an executable owned by root can give attackers a possible attack vector to become root._

In this challenge, we had to set SUID of `/challenge/getroot` using `chmod a+s` and retrieve the flag

### Flag
`pwn.college{oTiKWeHuySPZeNN5pF4SI9wSCNv.dNTM2QDL3kjM2czW}`

# Summary
1. We can access the permissions of a file/directory using `ls -l`.
2. 1. The File Type\
   The first character of each line represents the file type(d or -)
   
   2. The Permissions\
   The next nine characters are the actual permissions of the file, further divided into 3-3-3.
    i.e permissions of ("owner"), ("group"), (other users and other groups)

   3. Ownership Information\
   There are two columns: one that shows the user who owns the file and the other shows the group who owns the file.
3.  The **change ownership** command `chown` is used to change the ownership of files i.e `chown [username] [file]`.\
     Typically, `chown` can only be invoked by the root user.
4. The `id` command is used to check what groups we are in.
5. Group ownership can be changed with the `chgrp` (change group) command.
6. Each character represent permission for a different type:
      1. `r` - user/group/other can read the file (or list the directory)
      2. `w` - user/group/other can modify the files (or create/delete files in the directory)
      3. `x` - user/group/other can execute the file as a program (or can enter the directory, e.g., using `cd`)
      4. `-` - nothing (or _cannot execute_)
7. The `chmod` command is used to ***change the file permissions***\
Syntax: `chmod [OPTIONS] MODE FILE *`\
8.  **We can zero out permissions with '-'**
9.  The **"Set User ID" (SUID)** permissions bit _allows the user to run a program as the owner of that program's file._
10.  _Note: Giving the SUID bit to an executable owned by root can give attackers a possible attack vector to become root._
