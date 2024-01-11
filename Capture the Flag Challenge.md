# CH01
In the first challenge there were 4 different files base on my strength and knowledge
I chose to work with media.txt

- Created a python code which reads Base64-encoded image data from a file,
decodes it, creates a PIL Image object, saves it to a file, and attempts to
display the image. If any issues occur during this process, it handles the
exceptions and prints an error message

![Read media data](https://github.com/Mays-M/Images-/blob/main/read_media.png)

- After running the program: python3 ch01.py
- Flag successfully found which was printed as a data in the picture that produced from the code that read the media data.
- Inside the image print the target flag
  
![Flag ch01](https://github.com/Mays-M/Images-/blob/main/flag_ch01.png)

# CH02

## Opition1 hi.zip

On Linux create a python code which will do the will open a zip file and try different password after fetch them from a popular password published by the hackers around the world saved in a list called ‘rockyou.txt’ :
- Unzip file ‘hi.zip’
- Go throw a set of the most popular passwords ‘rockyou.txt’ used in the world.
- The program will try to every password in the list to open access zip file and the correct password will print it.
- The correct password was 'topsecret1’. Proceed with further actions.

![Python code ](https://github.com/Mays-M/Images-/blob/main/ch02_op1.png)

At this point after we knew the correct password will Unzip file type the content
of hi.txt by:
- Unzip hi.zip
- cat hi.txt
- will print a text seems to be encrypted: ZmxhZ3ttQlVMUFh5M1pkS1lhTnd9
- Navigate https://cyberChef.com to encode base64.
- Found the flag: flag{mBULPXy3ZdKYaNw}

![Encrypt  ](https://github.com/Mays-M/Images-/blob/main/ch02_flag.png)


## Option2 Brup.xml
Steps:
1. Download xml file and navigate to burp.xml
2. First notice the request and response are encrypted base64.
3. Navigate https://gchq.github.io/CyberChef/
4. Copy paste the request and decode from base64
- Request encrypted base64
- Resqust decrypted from base64
- Nothing interesting
5. Repeat Copy paste the Response and decode from base64.
- Response encrypted base64
- Responsedecrypted from base64
- In the response it return 200k successful and I started to digging to the code and soon I noticed there is encrypted link with a rel=flag which I
copied and base it to decoded base 64 and flage found: flag{sLpufQN9MK9x7Cb}

![oprtion 2 ](https://github.com/Mays-M/Images-/blob/main/ch02_op3.png)

![oprtion 2 ](https://github.com/Mays-M/Images-/blob/main/ch02_op3_flag.png)

## flag CH02
- Convert both option 1 and 2 with "flag 1" and "flag 2" to binary.
- Apply the XOR operation.
- Convert the result to hexadecimal.
- The discovered flag is:
00000000001E0E25393609370A172F7221560D1500

  # CH03 Flappy.html
  Steps:
1. Open the "flappy.html" file.
2. Right-click and select "Inspect" to examine the code.
3. Initially, my focus was on identifying the values of certain strings, which I proceeded to save in a separate file.
4. A particularly intriguing function caught my attention, prompting further investigation. Given the presence of hints in the challenge with multiple choices, I began analyzing the function named "doGravity."
- The doGravity function seems to be a bit obfuscated, and it's using base64 encoding and decoding functions (atob and btoa). Let's break down the function and see what values it produces.
- - If g is less than 1:It uses f1 to decode a string composed of myGamePiece.gravStr + myId + 'EZWRExkOHI2REN9'.
- If g is greater than or equal to 1: (this choice was mentioned in the challenge)
✓ It checks if myGamePiece.gravFunc is equal to f2 (btoa :decode base 64).
✓ If true, it uses f1 to decode a string composed of (myId || 'VGh') + myGamePiece.gravStr + 'EZWRExkOHI2REN9'.
✓ If false, it uses f1 to decode a string composed of ('VGh' || myId) +
myGamePiece.gravMod + 'VuY3Rpb24gaXMgaW5jb3JyZWN0'.


function doGravity(g=-1, f1=atob, f2=btoa) {
 return g < 1
 ? f1(myGamePiece.gravStr + myId + 'EZWRExkOHI2REN9')
 : ( myGamePiece.gravFunc == f2
 ? f1((myId || 'VGh') + myGamePiece.gravStr + 'EZWRExkOHI2REN9')
 : f1(('VGh' || myId) + myGamePiece.gravMod +


 5. Analysing to the function and examine the choices results.

    ![Notes ](https://github.com/Mays-M/Images-/blob/main/notes.png)
    
 7. Flag successfully found from choice (myId + myGamePiece.gravStr + 'EZWRExkOHI2REN9) by decode base64: flag{jKX4DFVDLd8r6DC}

      ![Notes ](https://github.com/Mays-M/Images-/blob/main/flag3.png)

