# Web Application Security
 
## Software and Data Integrity Failures:
### JuiceShop – Allowlist bypass
**Title:** Enforce a redirect to a page you are not supposed to redirect 

**Description:** It is possible to create a redirects URL with unvalidated special when a web App
accepts untrusted input that could redirect the request to URL.

**Steps to produce:****

1. Navigate to https://wasdat.fi/3000.
2. Right click to navigate to Inspect code of the website.
4. On the Debugger, there is a file called main.js.
5. CTRL +F, type ‘redirect’ from this we can file list of redirect URL and to try to navigate to it.
6. So it seems from the URL found it is http://wasdata.fi:3000/redirect?to= and then the
website we want to navigate, but it isn’t work directly
http://wasdata.fi:3000/redirect?to=google.com : received 406 error.
7. To successfully pass the websites, you need to redirect the URL to navigate like in the
example.
 google.com.

http://wasdata.fi:3000/redirect?to=https://www.google.com/?powned=https://github.com/bk
imminich/juice-shope


**Impact estimation:** High Severity: If no validation is applied, a malicious user could create a hyperlink
to redirect your users to an unvalidated malicious website.

**Mitigation:** Avoid using redirects URL and if you used don’t allow the user input for destination,
user should add his name as possible to prevent attack tampering with URL.


## Remote Code Execution (RCE)
### Main target – Deserialization of Untrusted Data
**Title:** Establish reverse shell using pickle Deserialization.

**Description:** An insecure deserialization attack has the capacity to inflict serious damage on your
application, putting its security in jeopardy and endangering sensitive data.

**Steps to produce:**
1. Navigate to http://wasdat.fi/api/import.
2. Test it by send “data=c2xlcCAxMAo=” to get 500 Internal Server Error  ![Testing](https://github.com/Mays-M/Images-/blob/main/test.png)
3. Create reverse shell using Pickle Deserialization in python.
4. Run the script to print pickled data.
5.  Send Post request to Api/import with the data value.![POST](https://github.com/Mays-M/Images-/blob/main/POST.png)
6.  Run netcat (nc) utility. It is a command used for network communication and
is commonly used to create a listening socket on a specific port for various purposes,
including network debugging and data transfer.
![netcat](https://github.com/Mays-M/Images-/blob/main/netcat.png)
**Impact estimation:** Medium SeverityAttacker can access to the server and read data shouldn’t be visible
to the user.

**Mitigation:** - Avoid using serialization, if you need to accept structured data from an HTTP request,
XML or JSON are more common formats and less prone to malicious use
- User-provided information, such as URL parameters, POST data, and cookies, should
always be treated as potentially unsafe. It is important never to unpickle data
originating from sources that are not authenticated or trusted.

**Visit** https://blog.securelayer7.net/insecure-deserialization-attack-in-python-application/
   
