# SHELL VARIABLES MODULE 7
The command line interface is colloquially referred to as a "shell" and programs written in this language are referred to as "shell scripts". The shell also supports variables and this module teaches about setting, printing and using these variables

## 1. Printing Variables
 `echo` is one of the commands that is used to print variables out. We can print out variables with `echo`, by prepending the variable name with a `$`. eg:
```
echo $PWD
/home/hacker
```
(PWD stores the current working directory)
  ### Flag
  `pwn.college{kMgF4iB5NopMXSWv93y11udL0VC.ddTN1QDL3kjM2czW}`

  ## 2. Setting Variables
  1. We can write values to variables using `=` 
  2. ***If you put spaces*** (e.g., VAR = 1337, VAR= 1337, VAR =1337), ***the shell won't recognize a variable assignment*** and will, instead, try to run the VAR command (which does not exist).
  3. The $ is only prepended to access variables i.e variable expansion.
     
     ### Flag
     `pwn.college{opEuX9yu3tgwlKNEwCfYiTziBp5.dlTN1QDL3kjM2czW}`
    
