# PONDERING PATHS MODULE 2
this module is based on "Linux File Paths"
Linux File System is a _"tree"_ where every `/` is a _"root"_ that can lead to more directories(folders) or files

## 1. The Root
basic `/` command to be implemented and flag is found

### Flag
`pwn.college{QlLwhiq7XVkXnSoY8HFPKmaacqX.dhzN5QDL3kjM2czW}`

## 2. Program and absolute paths
This challenge involved implementing **absolute paths** where challenge was a _directory_ and run was a _program_
I invoked `/challenge/run cd /challenge/run` as an absolute path to find the flag.
Typing the _absolute path_ ensures that I will always find the right directory andit doesnt really matter in wich directory I am in

### Flag
`pwn.college{YTPwOhaQF9LzyzWpFQ2i-UAx0Eg.dVDN1QDL3kjM2czW}`

## 3. Position thy self
This challenge was good, which involved going into a different directory using the `cd` command which stands for 'c'hange 'd'irectory.
After getting the answer of the directory where the flag was we just had to enter the absolute path to find the flag.
Another important hing that the challenge covers is the functionality of `~`: to show the current path at which the shell is located at.

### Flag
`pwn.college{0eKjskZjheEDZ8f1gz9wosggcAz.dZDN1QDL3kjM2czW}`

## 4. Position elsewhere
This challenge involved changing the directory to find the flag
1. We type in the _absolute path_ cd _absolute path_
2. We get the location where the flag is stored
3. We use `cd`  to navigate through the right directory
4. On reaching the directory we got the flag!

### Flag
`pwn.college{IlwyHxnEULihT77X7M_EUjXh-Hs.ddDN1QDL3kjM2czW}`

## 5. Position yet elsewhere
This is yet another variation of (3) and (4) changing the directory (going from existing directory to the destination directory) to find the flag.

### Flag
`pwn.college{c9OWDDn4ftOWDK8uu4aIFENdgHK.dhDN1QDL3kjM2czW}`

## 6. implicit relative paths, from /
We learnt about absolute paths, now we learn about relative paths.
Relative Paths only refer to those paths of the **cwd** i.e. current working directory. 
Relative Paths dont start off with `/` i.e root.

Here we just had to specify the root / in the command prompt first, and then type challenge/run

### Flag
`pwn.college{Q-w6OXghE07xJ7JGIc69Q2w-iJs.dlDN1QDL3kjM2czW}`

## 7. explicit relative paths, from /
In the prev challenge, our relative path directly specified the directory to descend into from the current directory i.e it was 'naked'.
Every directory has two implicit entries that you can reference in paths: `.` and `..`
Here we had to explicitly invoke the command using ./ i.e after going into the root directory we had to use `./challenge/run` to find the flag

### Flag
`pwn.college{gCuO_fVXIEjuf4D7joM0DHz3ggT.dBTN1QDL3kjM2czW}`

## 8. implicit relative path
It is important to understand that sometimes core system utility files can have the same names as the file which we want to open. In order to prevent the user from accessing the core system utility files, it does not allow user to directly give the `/` command. Linux returns an error saying `bash: run: command not found`
We need to explicitly specify what we want using `./`
This was the main point of this challenge.

### Flag
`pwn.college{8kEiOENZpbZzIZFkd6m4ce-Cj62.dFTN1QDL3kjM2czW}`

## 9. home sweet home
This challenge explains about `~` being the current working directory and how it is used to specify the `/home/hacker` path. 
It acts as a shorthand operator. `/home/hacker` will also be the default directory .
An important point to note is that expansion of `~` is an absolute path.

In this challenge we had to go to `/challenge` directory then invoke run explicitly using `./` and pass an argument to copy the flag into the `~` directory satisfying all the conditions 
I did this using : `./run ~/a` and the flag content was copied!!

### Flag
`pwn.college{gmOf294mapDeoy1XhqTrPc6WEuj.dNzM4QDL3kjM2czW}`

# Summary
1. Linux File System is a _"tree"_ where every `/` is a _"root"_ that can lead to more directories(folders) or files
2. The style of path, one that starts with the root directory, is referred to as an "absolute path".
3.  _absolute path_ ensures that I will always find the right directory andit doesnt really matter in wich directory I am in
4.  `cd` command stands for 'c'hange 'd'irectory.
5.  functionality of `~`: to show the current path at which the shell is located at.
6.  Relative Paths only refer to those paths of the **cwd** i.e. current working directory. Relative Paths dont start off with `/` i.e root.
7. relative path directly specified the directory to descend into from the current directory i.e it was 'naked'.
8. Every directory has two implicit entries that you can reference in paths: `.` and `..`
9. In order to prevent the user from accessing the core system utility files, it does not allow user to directly give the `/` command. Linux returns an error saying `bash: run: command not found`
We need to explicitly specify what we want using `./`
10. `/home/hacker` will be the default directory where all personal files are stored.



