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
