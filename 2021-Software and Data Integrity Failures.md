# Web Application Security
 
## Software and Data Integrity Failures:
### JuiceShop – Allowlist bypass
** Title:** Enforce a redirect to a page you are not supposed to redirect 

** Description:** It is possible to create a redirects URL with unvalidated special when a web App
accepts untrusted input that could redirect the request to URL.

** Steps to produce:****

1. Navigate to https://wasdat.fi/3000.
2. Right click to navigate to Inspect code of the website.
3. On the Debugger, there is a file called main.js.
4. CTRL +F, type ‘redirect’ from this we can file list of redirect URL and to try to navigate to it.
5. So it seems from the URL found it is http://wasdata.fi:3000/redirect?to= and then the
website we want to navigate, but it isn’t work directly
http://wasdata.fi:3000/redirect?to=google.com : received 406 error.
6. To successfully pass the websites, you need to redirect the URL to navigate like in the
example.
 google.com.

http://wasdata.fi:3000/redirect?to=https://www.google.com/?powned=https://github.com/bk
imminich/juice-shope


** Impact estimation:** High Severity: If no validation is applied, a malicious user could create a hyperlink
to redirect your users to an unvalidated malicious website.

** Mitigation:** Avoid using redirects URL and if you used don’t allow the user input for destination,
user should add his name as possible to prevent attack tampering with URL.
