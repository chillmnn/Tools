# List of helpful Windows cmds.

### List information about the system.
```
systeminfo
```

### List currently installed KBs.
```
wmic qfe get Caption,Description,HotFixID,InstalledOn
```

| Built-in Command-Line Command | Result |
|-------------------------------|--------|
| ```dir /h``` | Get help with the dir command. |
| ```dir *.xlsx /s``` | Search the current directory and all subdirectories for Excel spreadsheets. |

ipconfig /all
	

Show all IP information for all interfaces.

ipconfig /displaydns
	

Display resolved DNS names.

arp -a
	

Display the ARP cache.

route print
	

Display the route table.

net user
	

List all users on this machine.

net localgroup administrators
	

List all members of the local administrators group.

net share
	

List all shares on this machine.
