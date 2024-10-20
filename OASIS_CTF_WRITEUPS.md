
# 1. QUENCH YOUR THIRST

## Approach
In this capture the flag question, there was a cipher text which was encrypted and we had to decode.\
After getting stuck on it for a long time, I realised that there was a link at the bottom, so i encrypted the entire thing by brute force\
I used the common english words like in, the, of, as etc to decode and match the letters and i realised that 4 letters were missing in the entire text i.e.  Y Q Z J\
So i used permutations and combinations (total of 24) to try and check the link\
This finally led me to a link: HTTPS://KATB.IN/YXNZORQJ which consisted of the flag for the question.

The actual solution to the question was:
to use the cipher identifier on boxentriq,\
then we will get some cipher and then enter it in and then get the decoded part.\
The link is altered though. So we figure out that Y Q Z J are repeated only once and that we can get the katbin link only if you find an optimum combination for them.

### Flag
`oasis{fr3qu3nt_j4!l_br34k1ng_m4k3s_!t_t00_3asy_fr}`

# 2. MO-SIKE

## Approach
In this challenge, a text file was given which consisted of various names of colours\
On counting using a program, i got to know there were 3036 colours, so it could be arranged into a 56x56 pixel image.\
I ttied getting the resulting image but each 56 pixel line was not getting printed on anew line instead it was continuing.\

After finally figuring out the pixel, I tried to google lens and search about the image and it led to pokemon and the glitvh in the emulator games of missingno being a rare pokemon

### Flag
`OASIS{missingno_pokemon}`

# 3. NOT NOICE

## Approach
This was a pretty cool challenge where we had to change the .wav file to a spectrogram. I used an online spectrogram converter and played around with some of the settings which lead to the spectrogram being more and more clearly visible and using that i found out the flag.\
There was little problem to replace the E with 3, S with 5; so i manually tried again and again and changed them to get the flag

### Flag
`OASIS{5P3CT0GR4M_15_TH3_C00L35T}`


