# Welcome to the Linux helpful command list.

### Decode Base64 from terminal.
```
base64 -d <filename.txt>
```

### Display is package is installed.
```
dpkg -s <package name>
```

### Secure copy a remote file to local directory
```
scp <RemoteUsername>@<IP>:C:/<RemoteDirectory>/<FileName>.zip /<LocalDirectory>/<LocalDirectory
```

### RDP using rdesktop.
```
rdesktop -u <UserName> -d <Domain> -p <Password>  <IP>:<PORT>
```

### Using curl to upload a file directly to upload point.
```
curl -X POST -F "submit:<value>" -F "<file-parameter>:@<path-to-file>" <site>
```
