# Reconnaissance and Scanning 
## Ip address:
- To discover our range of network: ipclac command
- find which network is accessible to determine out: whatweb

  ## Enumeration the target
  - To check which port open on the target machine: nmap -A http://traget_IP
  - Enumerate the site we use command:  disb Target_IP

## Services

The scan indicated there were two services running on the host system. These were
Samba on ports 139 and 145 and Elasticsearch on port 9200. Elasticsearch is an opensource search and analytics engine.
Directory-buster also indicated an index.php file was available in addition to the
index.html

 ## Vulnerabilities
 
The services running on ports 139 and 445 utilize the NetBIOS-SSN service, a legacy
protocol known for its security vulnerabilities. port 9200 was identified as a more
promising attack vector due to its utilization of the HTTP protocol. This directed
attention towards uncovering vulnerabilities associated with the Elasticsearch
engine. Vulnerability scans were conducted using Metasploit, leveraging its userfriendly keyword-based interface within the terminal for enumerating and exploiting
vulnerabilities. Specifically, the search command was employed to facilitate the
process.

## Exploitation

The exploitation was by using Metasploit with the commands.
Use elasticsearch_traversal : selected the exploit to access the host’s target to search
for sensitive information, The command set rhost 192.168.1.100 selected the target IP
address. The command set port 9200 selected the target port

the exploit is successfully access the target system and downloaded a file which is a
list of users which was jarmo and remoteroot.

These clearly came from the /etc/passwd directory. If the /etc/passwd directory was
accessible it would also be possible to access password hashes located in the shadow
directory. This was achieved by modifying the filepath of the attack using the set
filepath /etc/shadow command.

The text file contained the password hash for the jarmo user. It also implied it would be
possible to gain root access using an SSH key pair.
The hash identifier indicate the hask password is SHA-256
