# Welcome to the Linux helpful command list.

### Decode Base64 from terminal.
```
base64 -d <filename.txt>
```

### DNS lookup of a mail server.
```
dig mx <domain.com>
```

### Display if package is installed.
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

### If /etc/shadow is writable, create a new password.
```mkpasswd -m sha-512 <password>```

### Some versions of Linux still allow hashes in /etc/passwd, create a new password.
```openssl passwd <password>```

### Linux enumeration using built-in bash.
| Local Linux Bash Command | Result |
|--------------------------|--------|
| ```uname -a``` | Show all available system information. |
| ```hostname``` | Show computer host name. |
| ```route``` | Show route table. |
| ```arp``` | Show ARP cache. |
| ```ifconfig``` | Show interface configuration, including IP address. |
| ```netstat -antp``` | Show TCP listening ports and socket status. |
| ```netstat -anup``` | Show UDP listening ports and socket status. |
| ```iptables -L``` | Display any firewall rules. |
| ```mount``` | Show mounted storage devices or file systems. |
| ```dpkg -l``` | List all packages installed on the system. |
| ```apache2 -v``` | List information about Apache2 web server. |
| ```mysql --version``` | List information about MySQL. |
| ```df -a``` | Show disk information. |
| ```cat /etc/*-release``` | Show distribution information. |
| ```cat /proc/cpuinfo``` | Show information about the CPU. |
| ```cat /etc/resolv.conf``` | List DNS servers host is using. |
| ```cat /etc/network/interfaces``` | List interface IP configuration. |
| ```cat /etc/passwd``` | List all users on the system. |
| ```cat /etc/group``` | List all groups on the system. |
| ```cat /etc/shadow``` | Show user hashes (privileged command). |
| ```users``` | List currently logged in users. |
| ```w``` | List currently logged in users and their processes. |
| ```lastlog``` | Show when all users last logged in. |
| ```whoami``` | Show current user name. |
| ```id``` | Show current user information. |
| ```sudo -l``` | List programs current user can run as root. |
| ```find / -iname *.txt``` | Find all txt files (case insensitive) in /. |
| ```find / -type f -exec grep -l "password" {} \;``` | List file names containing the word "password". |
| ```find . -type f -name ".*"``` | Find all hidden files. |
|```find / -user root -perm /4000``` | Find SUID permissions. |

"find | head" Find all files in the current directory and sub-directories.

### Linux Metasploit commands with post/linux/enum_system module
* enum_configs
* enum_network
* enum_protections
* enum_users_history

# Sensitive Linux Files
| File | Description |
|------|-------------|
| GRUB (/boot/grub) | Most commonly used bootloader package that loads the Linux kernel. |
| /etc/passwd | List of all local accounts. |
| /etc/shadow | Password hashes for all local accounts. |
| /etc/group | List of all local groups. |
| /etc/gshadow | Password hashes for local groups. |
| /proc/cmdline | Kernel parameters. |
| /etc/rc.* | Run commands. |
| /etc/profile | Sets system-wide environment variables on user shells. |
| /etc/hosts | Host-name-to-IP mappings—checked before DNS for name resolution. |
| /etc/resolv.conf | Lists DNS servers for system to use. |
| /etc/pam.d | Password and lockout policies. |
| ~/.bash_profile, ~/.bash_login, ~/.profile, /home/user/.bashrc, /etc/bash.bash.rc, /etc/profile.d | Possible locations to insert a script that will run when the shell starts. |

### Covering Tracks
* ```echo "" > /var/log/syslog``` Example of clearing the entire syslog.
* ```sed -i '/<KEYWORD>/d' /var/log/auth.log``` Using sed to delete all lines matching the given string while keeping the other lines intact.
* ```export HISTSIZE=0``` Setting the command history to zero before executing the commands.
* ```echo "" > ~/.bash_history and history -c``` In case the system has already recorded a shell history and you want to delete it.
* ```shred -zu /root/keylog.bin``` Will overwrite the file with zeros to hide the fact that it was shredded, then the file will be removed.
* ```file.docx -z "08/11/2019 18:22:06"``` You can use the timestomp command in Meterpreter to change MACE values.
