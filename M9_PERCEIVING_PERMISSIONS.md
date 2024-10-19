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

## 4. 
###
