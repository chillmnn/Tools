# Nessus

### Reset password.
```
sudo /opt/nessus/sbin/nessuscli chpasswd <username>
```

### Nessus has detected that API access on this scanner is disabled.
Stop the Nessus service.
```
sudo service nessusd stop
```

Reset the configuration.
```
sudo /opt/nesssus/sbin/nessuscli fix --reset
```

Start Nessus service.
```
sudo service nessusd start
```

Register Nessus using your previous registration key.
```
sudo /nessus/sbin/nessuscli --register <XXXX-XXXX-XXXX-XXXX-XXXX>
```

### Launch Nessus
```
sudo /bin/systemctl start nessusd.service
```

### Access Nessus
```
https://localhost:8834/
```
