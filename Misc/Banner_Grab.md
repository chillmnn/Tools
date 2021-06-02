# Banner Grabbing

### Useful ways to banner grab.

```
telnet <target IP> <port number>
```

```
echo -en "GET / HTTP/1.0\n\n\n"|nc www.<website.org> 80|grep Server
```

```
nc –vv <target IP> <port number>
```

```
nmap -sV <target IP> -p <port number>
```

```
nmap -sV --script=banner <target>
```
