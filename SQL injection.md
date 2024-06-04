# Web Application Security
 
## Identification and Authentication Failures: 

### JuiceShop – Login Björn
**Title:** : Unauthorized user can login to other users account and access their information with using OAuth 

**Description:** Login in with Bjoern’s Gmail account without previously changing his password,
applying SQL injection, or hacking his Google account.

**Steps to produce:****

1. Navigate to https://wasdat.fi/3000.
2. Login with administration rights using xxs injects
 Email: admin' or 1=1;--
 Password: admin' or 1=1;--
3. Navigate https://wasdat.fi/3000/#/administration
4. Find the target email: bjoern.kimminich@gmail.com.
5. Logout from admin account.
6. Navigate again https://wasdat.fi/3000.
7. On the source code, search for word ‘OAuth’ to find if it has any sensitive information.
From this digging in the source code, I found some interesting information with login using
email and password:

<code style="color : ligthskyblue">

ngOnInit() {
 var e = this;

this.userService.oauthLogin(this.parseRedirectUrlParams().access_token).subscribe(
 n => {
 const i = btoa(n.email.split('').reverse().join(''));
 this.userService.save({
 email: n.email,
 password: i,
 passwordRepeat: i
 }).subscribe(() => {
 this.login(n)
 }, () => this.login(n))
 },</code>

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
   
