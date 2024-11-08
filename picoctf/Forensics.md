# Forensics

## Challenge 1: tunn3l v1s10n

### A. Flag
`picoCTF{qu1t3_a_v13w_2020}`
![image](https://github.com/user-attachments/assets/ae855ed8-8565-4cf4-8a37-5383aa14f475)

### B. Approach
1. First opened 'tunn3l v1s10n' in notepad only to find out that it is a list of file signatures as notepad couldnt read it and many parts had 'SP' written which meant space.
2. Then, Opened the 'tunn3l v1s10n' file in a Hex Editor (https://hexed.it/) to check the contents of the file signature/ magic bytes
3. `42 4D` helped to know the file type which was BMP OR BITMAP file.
4. Viewed the file on PhotoPea as it could open BMP type file
5. On opening, the image was distorted / looked like some part of the picture was missing
6. Went back to Hex Editor and changed the height of the file to match to the width\
   (attached below is the screenshot where height was changed)
   ![image](https://github.com/user-attachments/assets/56bfa813-c945-4d64-8080-c6ca769d13ab)
7. Opened this changed file back in PhotoPea to find the flag

### C. Concepts Learned
1. **File Signatures/ Magic Bytes**
   1. Magic bytes, also referred to as magic numbers or file signatures, are sequences of bytes located at the beginning of a file.
   2. They serve as a unique identifier for the file’s format or type.
   3. `42 4D` was the identifier for Bitmap File
  
2. **Bitmap Files**
   1. The BMP format is an uncompressed raster file designed to display high-quality images on Windows and store printable photos.
   2. Raster format means that the images they contain are made of pixels.
   3. This lets BMPs store images with a wide array of colors and details, making them ideal for high-quality 2D digital photographs. 

3. **Changing resolution through hex editor**
   The width starts at hex offset 12, lasts for 4 bytes, and is followed by the height at offset 16, which is also 4 bytes.

### D. Mistakes
1. First mistake was to not understand the file type, trying to open in various other apps- notepad, vs code...
2. Changing all options in Photopea only to understand that the hex file content needs to be changed to be reflected onto the digital image.

### E. References
1. Lots of trial and error lead to the final answer
2. https://en.wikipedia.org/wiki/List_of_file_signatures helped the most to know the meaning about different codes.
3. https://www.adobe.com/creativecloud/file-types/image/raster/bmp-file.htm
