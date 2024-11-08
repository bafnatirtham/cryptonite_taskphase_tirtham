# Reverse Engineering

## Challenge 1: Vault door 3

### A. Flag
`picoCTF{ju5t_a_s1mpl3_an4gr4m_4_u_79958f}`

### B. Approach
In this challenge, were given a java code, which takes password as input from the user and changes it according to modifications as specified in the code

Some main points extracted after having a look at the code were as follows
1. The program checks if the string/password inputted is strictly 32 characters long or not. If len(string) != 32 then the program does not function
2. The first 8 characters (0 to 7) are written as it is in the encrypted format of the password
3. The next 8 characters (8 to 15) are simply reversed using logic `23-i` (i=8 to 15) which will give 15,14,13....8
4. The next 16 characters are modified using odd and even logic
   1. All even characters i.e index 16,18,20...,28,30 are modified using the logic `46-i` i.e changed to 30,28,26....16\
      so the character at index 16 is to be replaced by character at index 30 and so on
   2. All odd characters i.e. index 17,19,21,.....,29,31 are written as it si without any changes

Using this logic, we can convert the output `jU5t_a_sna_3lpm18g947_u_4_m9r54f` into the originally inputted password which is:\
`ju5t_a_s1mpl3_an4gr4m_4_u_79958f`

### C. Concepts Learnt
1. Basic reading and logic used by for-loops
2. String/character array manipulation to encrypt the given string
3. Brushed up the concepts and use of indexes in array.

### D. Mistakes
No such mistakes in the logic for solving, just mistook l for 1 while changing the string.

### E. References
Previous knowledge of for loops and string manipulation



