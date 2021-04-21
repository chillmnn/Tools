# smbclient

### List shares.
```
smbclient -L \\\\<IP> -U <Username>
```

### Connect to a listed share share.
```
smbclient \\\\<IP>\\C$ -U <Username>
```
