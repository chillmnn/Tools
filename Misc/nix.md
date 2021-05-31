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

### Linux enumeration using built-in bash.
| Local Linux Bash Command | Result |
|--------------------------|--------|
| ```uname -a``` | Show all available system information. |
| ```hostname``` | Show computer host name. |

route
	

Show route table.

arp
	

Show ARP cache.

ifconfig
	

Show interface configuration, including IP address.

netstat -antp
	

Show TCP listening ports and socket status.

netstat -anup
	

Show UDP listening ports and socket status.

iptables -L
	

Display any firewall rules.

mount
	

Show mounted storage devices or file systems.

dpkg -l
	

List all packages installed on the system.

apache2 -v
	

List information about Apache2 web server.

mysql --version
	

List information about MySQL.

df -a
	

Show disk information.

cat /etc/*-release
	

Show distribution information.

cat /proc/cpuinfo
	

Show information about the CPU.

cat /etc/resolv.conf
	

List DNS servers host is using.

cat /etc/network/interfaces
	

List interface IP configuration.

cat /etc/passwd
	

List all users on the system.

cat /etc/group
	

List all groups on the system.

cat /etc/shadow
	

Show user hashes (privileged command).

users
	

List currently logged in users.

w
	

List currently logged in users and their processes.

lastlog
	

Show when all users last logged in.

whoami
	

Show current user name.

id
	

Show current user information.

sudo -l
	

List programs current user can run as root.

find | head
	

Find all files in the current directory and sub-directories.

find / -iname *.txt
	

Find all txt files (case insensitive) in /.

find / -type f -exec grep -l "password" {} \;
	

List file names containing the word "password".

find . -type f -name ".*"
	

Find all hidden files.

### Linux Metasploit commands with post/linux/enum_system module
* enum_configs
* enum_network
* enum_protections
* enum_users_history

