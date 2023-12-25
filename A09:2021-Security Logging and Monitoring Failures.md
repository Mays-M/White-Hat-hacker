# Web Application Security

## Security Logging and Monitoring:
### JuiceShop – Exposed Metrics

**Title:** Find the endpoint that serves usage data to be scraped by a popular monitoring system.

**Description:** Applications cab publish ‘/metrics’ endpoint available to all users and can exposes
sensitive information about the applications.

**Steps to produce:**
1. Navigate to http://wasdat.fi:3000/#/score-board.
2. On the board score there is a link about Prometheus, read about the Prometheus and
explore it.
3. Navigate to https://prometheus.io/docs/prometheus/latest/getting_started/
To learn more about Prometheus
“Prometheus should start up. You should also be able to browse to a status page about itself
at localhost:3000. Give it a couple of seconds to collect data about itself from its own HTTP
metrics endpoint.
You can also verify that Prometheus is serving metrics about itself by navigating to its
metrics endpoint: localhost:3000/metrics “
4. So, we learned applications published endpoint called ‘/metrics’ , can be navigate directly
by http://wasdat.fi:3000/metrics
5. We explored sensitive information on the website and solved the challenge.
   
**Impact estimation:**
– Medium Severity: Malicious user can learn sensitive information shouldn’t be
validation to user.

**Mitigation:**
– Avoid letting user access to use metrics, the link should be less generic and not
default with restricting access list of IPs.
---------------------------------------------------------------------------------------------------------------------

## Main target – Insert of Sensitive Information into Log File
**Title:** Find sensitive information from the Django logs and login with easily guessable credentials
according to log.

**Description:** Log files are essential components of a system or application, and they serve several
important purposes, each with its own impact.

**Steps to produce:**
1. Navigate to http://wasdat.fi.
2. On the console :
• Ssh wasdat.fi@192.168.1.101: ssh connection the docker.
• Docker ps: list all the containers and identified our target container.
• Docker exec -it 7bc2b13497bb /bin/bash: login to the Django container.
3. By default, if want to find the log files, you can find the filename parameter in handlers of
the file ‘settings.py’
4. From the log error file, I assumed if the user tried to login with username: John to John5
and stopped so maybe if I tried John6 I can successfully login while I have the correct
password.
5. Successfully guessed information from the extracted log and login with John6: john88
FLAG{was_1_2_3_5_taken}

**Impact estimation:**
– Medium Severity: logs files can be a tool to the attackers to use to find sensitive
information about the application or user credential information.
**Mitigation:**
- by implementing a security measure such encryption and permissions, you can help
protect log files from hacking attempts and maintain the integrity and confidentiality of
log data. It's important to regularly assess and update your log file security practices to
adapt to evolving threats and vulnerabilities.
**Visit** https://stackoverflow.com/questions/19256919/location-of-django-logs-and-errors
