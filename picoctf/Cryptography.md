# Cryptography

## Challenge 1: Mini RSA

### A. Flag
`picoCTF{e_sh0u1d_b3_lArg3r_7adb35b1}`

### B. Approach
1. I opened the cyphertext file in NOtepad to find the cyphertext value(c), e value as 3 and n value (n=p*q where p and q are primes)
2. I learnt about what RSA is through the wikipedia link given in the Hints of picoCTF
3. On reading through the page, under "Attacks under plain RSA", I came acroos the point\
   _"When encrypting with low encryption exponents (e.g., e = 3) and small values of the m (i.e., m < n^(1/e)), the result of m^e is strictly less than the modulus n (m^e < n). In this case, ciphertexts can be decrypted easily by taking the eth root of the ciphertext over the integers."_
4. But since in this challenge, m^e is slightly larger than n, so we can approximate using integer math that: M^e =kN+C where k is a small integer.
5. This means you are looking for the smallest 𝑘 such that 𝑀^𝑒 divided by 𝑁 yields a remainder 𝐶.
6. Using this I found the decryption code by running k through 1 to x using the follwoing code in python, after installing gmpy2.

   Code:
   ```
   from gmpy2 import iroot
    upper_bound = 100000  # Initial guess; adjust if needed
    for k in range(1, upper_bound):
        M, exact = iroot(C+ k*N, e)
        if exact:
            print("Decrypted plaintext:", M)
            break
    else:
        print("increasing the upper bound.")
    ```
7. Using this I found the plaintext of RSA. I converted this plain text into hexadecimal format and then into ASCII format to get the desired flag
   ```
   # Given plaintext integer
    plaintext_int = x;
    
    # Convert integer to hexadecimal
    hex_representation = hex(plaintext_int)[2:]  # Remove the '0x' prefix
    
    # Ensure the length is even (optional)
    if len(hex_representation) % 2 != 0:
        hex_representation = '0' + hex_representation
    
    # Convert hexadecimal to ASCII
    ascii_representation = bytes.fromhex(hex_representation).decode('utf-8', errors='ignore')
    
    # Print the ASCII string
    print("Decoded plaintext:", ascii_representation)
   ```

### C. Concepts Learnt
1. RSA: (Rivest–Shamir–Adleman) is a public-key cryptosystem\
   An RSA user creates and publishes a public key based on two large prime numbers, along with an auxiliary value. The prime numbers are kept secret. Messages can be encrypted by anyone, via the public key, but can only be decrypted by someone who knows the private key
2. The keys for the RSA algorithm are generated in the following way:
   1. Choose two large prime numbers p and q. p and q are kept secret.
   2. Compute n = pq.
   3. Compute λ(n), where λ is Carmichael's totient function; **λ(n) = lcm(p − 1, q − 1).**; λ(n) is kept secret.
   4. Choose an integer e such that 1 < e < λ(n) and gcd(e, λ(n)) = 1; that is, e and λ(n) are coprime. e is released as part of the public key.
   5. Determine d as d ≡ e^(−1).(mod λ(n)); that is, d is the modular multiplicative inverse of e modulo λ(n). d is kept secret as the private key exponent
      ![image](https://github.com/user-attachments/assets/958f19f4-204d-4b7c-b636-6dd4fbef514f)
      ![image](https://github.com/user-attachments/assets/0517b034-8381-44a3-b7e7-12832967d331)

3. **gmpy2** is a Python extension module that supports fast multiple-precision arithmetic12345. It provides support for integer, rational, real, and complex numbers with arbitrary precision2. You can use gmpy2 to perform high-precision arithmetic and have control over rounding modes
4. **Need for converting plaintext--> hex format--> ascii format**
   1. Directly converting a large plaintext integer to ASCII is not feasible because ASCII characters are represented by bytes, not by large integers.
   2. If you try to directly convert a large integer to ASCII without interpreting it as bytes, Python would attempt to decode the integer as a single number, which does not map directly to a series of characters. ASCII decoding expects a sequence of bytes, not an integer
   3. Hexadecimal Representation: When you convert the integer to hexadecimal, it breaks down the integer into a series of byte-like pairs (e.g., 41, 42, etc.), which can each be mapped directly to ASCII characters.
   4. Byte Alignment: Hexadecimal makes it easy to identify byte boundaries since each pair of hex digits represents one byte. Converting these byte pairs to characters using bytes.fromhex() and .decode('utf-8') translates them into a human-readable string like hello.
  
### D. Mistakes Made
1. directly tried to find the e th root of N to find C only to realise that M^e was slightly larger than N.
2. Not seeing the extra spaces in the dercypted string and pasting half of the flag.

### E. References
1. https://en.wikipedia.org/wiki/RSA_(cryptosystem)
2. https://www.pythonpool.com/rsa-encryption-python/


## Challenge 2: miniRSA

### A. Flag
`picoCTF{n33d_a_lArg3r_e_606ce004}`

### B. Approach
1. Using information from miniRSA challenge and learning about the working of RSA encryption from the references provided in the hints,
2. I opened the cyphertext in notepad to find the values for N(=p*q), cyphertext (c) and integer 'e'
3. Since e was very small (e=3), my first attack and intuitive thought on RSA decryption was to find the e th root of C
4. Code:
   ```
   from gmpy2 import iroot

   # Given values
   ciphertext = 
   e=3
   # Compute the cube root of the ciphertext
   m, exact = iroot(ciphertext, e)
   
   
   if exact:
       hex_representation = hex(m)[2:]  # Remove '0x' prefix
       if len(hex_repn) % 2 != 0:
           hex_repn = '0' + hex_repn  # Ensure even-length for proper byte conversion
   
       # Convert hexadecimal to ASCII
       plaintext = bytes.fromhex(hex_repn).decode('utf-8', errors='ignore')
   
       print("Decrypted plaintext:", plaintext)
   else:
       print("Cube root was not exact. Decryption may not be correct.")
   ```
### C. Concepts Learnt 
1. RSA
2. Conversion of plaintext into hexadecimal format and then into ASCII (readable) format

### D. Incorrect Methods
none

### E. References 
1. https://en.wikipedia.org/wiki/RSA_(cryptosystem)
2. https://www.pythonpool.com/rsa-encryption-python/
   
