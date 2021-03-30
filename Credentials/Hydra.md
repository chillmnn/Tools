# Hydra

## Helpful Links

https://en.kali.tools/?p=220

### In order to use Hydra you must specify the service (protocol) that is being attacked, the username and provide a password list.
In this example below the protocol is FTP, the username is Fred and the password list is rockyou.txt.
```
hydra -l Fred -P rockyou.txt ftp://<IP>
```

### FTP Bruteforce
```
hydra -t 4 -l <username> -P <path to wordlist> -vV <IP> ftp
```
FTP Options
* ```-t 4``` specifies number of threads to use

* ```-l [user]``` specifies username

* ```-P``` specifies password list

* ```-vV``` very verbose mode, shows the login/pass combination for each attempt

* ```ftp``` sets the protocol

### SSH
```
hydra -l <username> -P <full path to pass> <IP> -t 4 ssh
```
SSH Options
* ```-l``` specifies username

* ```-P``` specifies password list

* ```-t``` specifies number of threads to use

### Post Web Form
You can bruteforce web forms also. To do this you must know if the request is a GET or POST. This can be found by looking at the source code developer tools under the Network tab.
```
hydra -l <username> -P <wordlist> <IP> http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V
```
Post Web Form Options
* ```-l``` specifies single username
* ```-P``` specifies password list
* ```http-post-form``` indicates type of form (POST)
* ```login url``` the login pages URL
* ```:username``` the form field where the username is entered
* ```^USERNAME^``` tells Hydra to use the username
* ```password``` the form field where the password is entered
* ```^PASS^``` tells Hydra to use the password list supplied earlier
* ```Login``` indicates to Hydra the login failed message
* ```Login failed``` is the login failure message that the form returns
* ```F=incorrect``` if this word appears on the page, its incorrect
* ```-V``` verbose output for every attempt

