# Web Application Security

## Insecure Design: 
### JuiceShop – Easter Egg

**Title:** : Find Easter Egg from Juice Shop.

**Description:** Web Application has a file to give instruction about the site and it is work as a robot
inside the site and sometimes this file can include a sensitive information or stored password.

**Steps to produce:**
1. Navigate to https://wasdat.fi/3000.
2. Login in to the website.
3. Navigate to https://wasdat.fi/3000/robots.txt.
4. The robots.txt file include information allowed to navigate to another page.
    user-agent:* ;means applies to all robots
   
Disallow: /ftp ; first place to look as it is disallowed
6. In the website : wasdat.fi:3000/ftp. Found an easter.gg file but it is open only as .md file or pdf. So, navigate to file and add %2500.md
7. The URL : wasdat.fi:3000/ftp/easter.gg%2500.md print a text file which included a further
information and got the score. 
   
**Impact estimation:**
– Low Severity: User/robot can identify restricted or confidential information on thesite and disallow list can serve as a map to the first place to look.

**Mitigation:**
– Ensure it is correctly configuring, understand the purpose of using robots.txt with your site, create user-agent and test the configuration. 

---------------------------------------------------------------------------------------------------------------------

### Main target – Insert of Sensitive Information into Log File
**Title:** Find sensitive information from the Django logs and login with easily guessable credentials
according to log.

**Description:** Log files are essential components of a system or application, and they serve several
important purposes, each with its own impact.

**Steps to produce:**

1. Navigate to http://wasdat.fi.
2. On the console :
• Ssh wasdat.fi@x.x.x.x: ssh connection the docker.
• Docker ps: list all the containers and identified our target container.
• Docker exec -it 7bc2b13497bb /bin/bash: login to the Django container.
3. By default, if want to find the log files, you can find the filename parameter in handlers of
the file ‘settings.py’
4. From the log error file, I assumed if the user tried to login with username: John to John5
and stopped so maybe if I tried John6 I can successfully login while I have the correct

password. ![LogFile](https://github.com/Mays-M/Images-/blob/main/logFile.png)


6. Successfully guessed information from the extracted log and login with John6: john88
   
FLAG{was_1_2_3_5_taken} ![Flag](https://github.com/Mays-M/Images-/blob/main/flag.png)



**Impact estimation:**
– Medium Severity: logs files can be a tool to the attackers to use to find sensitive
information about the application or user credential information.


**Mitigation:** by implementing a security measure such encryption and permissions, you can help
protect log files from hacking attempts and maintain the integrity and confidentiality of
log data. It's important to regularly assess and update your log file security practices to
adapt to evolving threats and vulnerabilities.

**Visit: ** https://stackoverflow.com/questions/19256919/location-of-django-logs-and-errors

