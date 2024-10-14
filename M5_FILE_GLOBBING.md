# FILE GLOBBING MODULE 5
This module teaches us about the functionality of globbing.
Globbing is used when we need to reference path instead of typing them again and again

## 1. Matching with *
1. When it encounters a '*' character in any argument, the shell will treat it as "wildcard" and try to replace that argument with any files that match the pattern.
2. It can match one, many or none of the files
3. When zero files are matched, by default, the shell leaves the glob unchanged
4. The * matches any part of the filename except for '/' or a leading '.' character

Using this info, i got the flag by using glob * to specify challenge to cd in less than 4 chars

### Flag
`pwn.college{IR4x-v6xUL_mQ6j9xq8gQRBmCSw.dFjM4QDL3kjM2czW}`

## 2. Matching with ?
When it encounters a ? character in any argument, the shell will treat it as single-character wildcard. This works like *, but only matches one character i.e if two ?? given then it will match two characters. eg: 
```
echo Look: file_?
Look: file_a file_b

echo Look: file_??
Look: file_cc
```
### Flag
`pwn.college{smHYqeASljt2dTK1tQB9gBX-Ybg.dJjM4QDL3kjM2czW}`

## 3. Matching with []
[] is a wildcard for some subset of potential characters, specified within the brackets. eg: [abc] will match files with char a/b/c

Using this info, i got the flag for this challenge
`pwn.college{ktFuZ-y9alIY5Rh6pRHIQ6iiF6-.dNjM4QDL3kjM2czW}`

## 4. Matching paths with []
we can also match paths with [] by specifying the path and then putting the part which we have to glob
`pwn.college{kz5Mm1goy4CciJG26IbeT7xTcK9.dRjM4QDL3kjM2czW}`

## 5. Mixing Globs
This challenge used all information from (1) to (4) to retrieve the flag

### Flag
`pwn.college{oNHVAqppupcDhzrhBkkBkQYnLhK.dVjM4QDL3kjM2czW}`


