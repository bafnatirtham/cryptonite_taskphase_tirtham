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

   ## 3. Multi-word Variables
  If we type 'var=100 data', it will only take 100 as the input for the var variable as there should be no space after the '=' sign. Thus, we need to quote the multiword variable i.e var="100 data"\
 Using this information I retrieved the flag.
 
 ### Flag
     `pwn.college{8_MpwQaLLI_KEA1HFhXFMBYUd7T.dBjN1QDL3kjM2czW}`

   ## 4. Exporting Variables
   Variables that you set in a shell session are local to that shell process i.e. other commands you run won't inherit them. 
   eg:
   ```
hacker@dojo:~$ VAR=1337
hacker@dojo:~$ echo "VAR is: $VAR"
VAR is: 1337
hacker@dojo:~$ sh
$ echo "VAR is: $VAR"
VAR is:
```
The $ prompt is the prompt of sh, a minimal shell implementation that is invoked as a _child of the main shell process_. And it does not receive the VAR variable.

For this, we use the `export` command. When we export variables, they are passed into the environment variables of child processes.

 ### Flag
 `pwn.college{QyRgXorzt2PcFR5G00nQJUgbjqO.dJjN1QDL3kjM2czW}`


 ## 5. Printing Exported Variables
The `env` command is used to print all the exported variables\
Using this information, I got the flag as:
### Flag
`pwn.college{kp5Wu35-JM1wPHD3pjKOHP4mJmF.dhTN1QDL3kjM2czW}`

## 6. Storing Command Output
We can store the output of a command using **"command substitution"**\
eg: FLAG=$(cat /flag) will store the output of /flag into FLAG variable.
We can also use backticks to execute this command i.e. 
```
FLAG=`cat /flag`
```

### Flag
`pwn.college{kXJcpadmR__DKhPKxvVwgDix8VE.dVzN0UDL3kjM2czW}`

## 7. Reading Input
The `read` command reads/accepts data from the standard input\
Basic Syntax: `read -p "INPUT: " MY_VARIABLE`

### Flag
`pwn.college{83v26LCG299nDSMchjt5PxSsyNj.dhzN1QDL3kjM2czW}`

## 8. Reading Files
We can accept files as input using `read` command instead of using cat, stdin and stdout
```
hacker@dojo:~$ echo "test" > some_file
hacker@dojo:~$ read VAR < some_file
hacker@dojo:~$ echo $VAR
test
```
 The example redirects some_file into the standard input of read, and so when read reads into VAR, it reads from the file.\

Command used to get the flag : `read PWN < /challenge/read_me`
 ### Flag
 `pwn.college{YjnGhoyXv7Rer0AlidGJrfwbO9e.dBjM4QDL3kjM2czW}`
