# Evil-WinRM

### Installation.
```
sudo gem install evil-winrm
```

### Basic usage.
```
evil-winrm -i <IP> -u <Target Username> -H <NT Hash, no colons>
```

Fred:500:a1a1a1a1a1a1a1a1a1a1a1a1a1a1a1a1:b2b2b2b2b2b2b2b2b2b2b2b2b2b2b2b2:::
 * Fred is the user
 * 500 is a relatice identifier (i.e. Administrator)
 * a1a1a1 is the LM hash
 * b2b2b2 is the NT hash
