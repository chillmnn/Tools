# List of helpful Windows cmds.

### List information about the system.
```
systeminfo
```

### List currently installed KBs.
```
wmic qfe get Caption,Description,HotFixID,InstalledOn
```

### Built-in command-lines that are helpful for enumeration.
| Built-in Command-Line Command | Result |
|-------------------------------|--------|
| ```dir /h``` | Get help with the dir command. |
| ```dir *.xlsx /s``` | Search the current directory and all subdirectories for Excel spreadsheets. |
| ```ipconfig /all``` | Show all IP information for all interfaces. |
| ```ipconfig /displaydns``` | Display resolved DNS names. |
| ```arp -a``` | Display the ARP cache. |
| ```route print``` | Display the route table. |
| ```net user``` | List all users on this machine. |
| ```net localgroup administrators``` | List all members of the local administrators group. |
| ```net share``` | List all shares on this machine. |

### Powerhell cmdlets useful for enumeration.
| PowerShell Cmdlet | Result |
|-------------------|--------|
| ```Get-Command``` | List all installed PowerShell cmdlets. |
| ```Get-Command Get-*``` | List all cmdlets that start with "Get". |
| ```Get-LocalUser``` | List all local users on the machine. |
| ```Get-LocalGroup``` | List all local groups on the machine. |
| ```Get-LocalGroupMember <group name>``` | List all members of the given group. |
| ```Get-Website``` | List websites on the machine. |
| ```Get-ChildItem``` | List items and child items in a folder or Registry key. |

"Get-ChildItem -Path C:\ -Include *.docx,*.xlsx,*.txt -File -Recurse -ErrorAction SilentlyContinue | Select-String password" Starting from C:\ recursively search every Word, Excel, and text file for the word "password", and display the path, file name, line number, and text on that line.

# Alternate Data Streams (ADS)

### This creates an empty file called test.txt, while simultaneously creating a hidden file called hidden.txt. 
```C:\>echo "Super secret info" > test.txt:hidden.txt```

### To view the secret message.
```C:\>notepad.exe test.txt:hidden.txt```

# Unquoted Service Paths

You can search for services that have this vulnerability using:

* Metasploit module ```exploit/windows/local/trusted_service_path```
* PowerSploit ```Get-ServiceUnquoted cmdlet```
* WMIC query ```wmic service get name,displayname,pathname,startmode |findstr /i “auto” |findstr /i /v “c:\windows\\” |findstr /i /v “””```

### Windows Account Manipulation
##### You will need administrator or SYSTEM level privilege to run some of these commands.

To Do This Action:
	

Run This Command:

List all users
	

net user

See information about guest
	

net user guest

Search the status of guest to determine if it's active (enabled) or not
	

net user guest | findstr /C:"active"

Activate (enable) guest
	

net user guest /active:yes

Set/change the guest password to Pa22w0rd
	

net user guest Pa22w0rd

Add guest to the local administrators group
	

net localgroup administrators /add guest

View the SID of each account
	

wmic useraccount get name,sid
