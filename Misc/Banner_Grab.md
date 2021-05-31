### Useful ways to banner grab.

```telnet 192.168.10.100 8000``` (After making the connection, press Ctrl+] to break, then enter quit)

```
echo -en "GET / HTTP/1.0\n\n\n"|nc www.<website.org> 80|grep Server
```
