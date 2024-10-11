# PONDERING PATHS MODULE 2
this module is based on "Linux File Paths"
Linux File System is a _"tree"_ where every `/` is a _"root"_ that can lead to more directories(folders) or files

## 1. The Root
basic `/` command to be implemented and flag is found

## 2. Program and absolute paths
This challenge involved implementing **absolute paths** where challenge was a _directory_ and run was a _program_
I invoked `/challenge/run cd /challenge/run` as an absolute path to find the flag.
Typing the _absolute path_ ensures that I will always find the right directory andit doesnt really matter in wich directory I am in

## 3. Position thy self
This challenge was good, which involved going into a different directory using the `cd` command which stands for 'c'hange 'd'irectory.
After getting the answer of the directory where the flag was we just had to enter the absolute path to find the flag.
Another important hing that the challenge covers is the functionality of `~`: to show the current path at which the shell is located at.

## 4. Position elsewhere
This challenge involved changing the directory to find the flag
1. We type in the _absolute path_ cd _absolute path_
2. We get the location where the flag is stored
3. We use `cd`  to navigate through the right directory
4. On reaching the directory we got the flag!

## 5. Position yet elsewhere
This is yet another variation of (3) and (4) changing the directory (going from existing directory to the destination directory) to find the flag.

## 6. implicit relative paths, from /
We learnt about absolute paths, now we learn about relative paths.
Relative Paths only refer to those paths of the **cwd** i.e. current working directory. 
Relative Paths dont start off with `/` i.e root.

Here we just had to specify the root / in the command prompt first, and then type challenge/run

## 7. explicit relative paths, from /
In the prev challenge, our relative path directly specified the directory to descend into from the current directory.
Every directory has two implicit entries that you can reference in paths: . and `..`

