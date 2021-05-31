# Nmap

## Helpful Links
https://nmap.org/book/nse-usage.html


https://nmap.org/nsedoc/

### By defualt nmap runs -sS when sudo is provided and by default runs -sT when no sudo is provided.

### Syn Scan or "half open" scan purposely sends RST flag to be more stealthy. Can cause issues on unstable devices.
```
nmap -sS <IP>
```

### TCP scan. This waits to receive RST flag from the target.
```
nmap -sT <IP>
```

### Scan UDP ports. If target doesn't respond to nmap you'll receive "open|filtered". If port is closed you'll receive "port unreachable".
```
namp -sU <IP>
```

### Detect OS
```
nmap -o <IP>
```

### Detect version of services
```
namp -sV <IP>
```

### Provide more information (increase verbosity), adding more v's increases verbosity of information.
```
nmap -v <IP>
nmap -vv <IP>
```

### Save out to three major formats. This is useful when reports need to be created. 
```
nmap -oA <IP>
```

### Save to normal format.
```
nmap -oN <IP>
```

### Save to "grepable" format.
```
nmap -oG <IP>
```

### Aggresive scan mode detects OS, traceroute, common script scanning. This is very loud and will alaram blue team. 
```
nmap -A <IP>
```

### Timing template where 1 is slowest and 5 being the fastest.
```
nmap -T5 <IP>
```

### Scan specific ports.
```
nmap -p 80, 53, 443, 445 <IP>
```

### Scan through specific range of ports.
```
nmap -p 889-1023 <IP>
```

### Scan all ports
```
nmap -p- <IP>
```

### Vulnerabiliy scan.
```
nmap --script=vuln <IP>
```

### Ping sweep with IP range or subnet.
```
nmap -sn <IP>
nmap -sn <IP/cidr>
```

### Timing template where 1 is slowest and 5 being the fastest.
```
nmap -T5 <IP>
```

### Less Common Scans - All 3 are similar and said to be stealthier than -sS for firewall evasion.
1. TCP Null ```nmap -sN <IP>``` the TCP request is sent with no flags set


2. TCP FIN ```nmap -sF <IP>``` the TCP request is sent with a FIN flag, usually to gracefully close conenction


2. TCP Xmas ```namp -sX <IP>``` sends malformed TCP flags PSH, URG, FIN.

### Use if you know target is online but acting as if it's offline. For instance if ICMP is blocked.
Use the following switches:
* ```-f```Used to fragment the packets making it less likely that the packets will be detected by a firewall or IDS.
* An alternative to ```-f```, but providing more control over the size of the packets: ```--mtu <number>```, accepts a maximum transmission unit size to use for the packets sent. This must be a multiple of 8.
* ```--scan-delay <time>ms``` used to add a delay between packets sent. This is very useful if the network is unstable, but also for evading any time-based firewall/IDS triggers which may be in place.
* ```--badsum``` this is used to generate in invalid checksum for packets. Any real TCP/IP stack would drop this packet, however, firewalls may potentially respond automatically, without bothering to check the checksum of the packet. As such, this switch can be used to determine the presence of a firewall/IDS.

### Nmap Scripting Engine (NSE)
```nmap --script=<script_name> <IP>```

### Multiple scripts can be seperated by commas, ex. --script=smb-enum-users,smb-enum-shares

Script help menu
```--script-help <script-name>```

Full list found here, https://nmap.org/book/nse-usage.html

* safe: Will not affect target.


* intrusive: Likely to affect target.


* vuln: Scan for vulnerabilities.


* exploit: Attempt to exploit a vulnerability.


* auth: Attempt to bypass auth for running service (e.g. logging into FTP anonymously)


* brute: Attempt to bruteforce credentials of running service.


* discover: Attempt to query service for more information about network.


### Searching for scripts.
There are two methods to search for an installed script. One by using the /usr/share/nmap/scripts/script.db file and the other method by using grep.
```
cd /usr/share/nmap/scripts/script.db
head script.db
```
or
```
grep "ftp" /usr/share/nmap/scripts/script.db
```
or
```
ls -l /usr/share/nmap/scripts/*ftp*
```
Same can be done for searching categories of scripts.
```
grep "discovery" /usr/share/nmap/scripts/script.db
```

### Installing new scripts.
Run if one script is missing locally.
```
sudo apt update && sudo apt install nmap
```
Run to install a single script manually (this must be followed with nmap --script-updatedb  which update the scripts.db file)
```
sudo wget -O /usr/share/nmap/scripts/<script-name>.nse https://svn.nmap.org/nmap/scripts/<script-name>.nse 
```
### Some scripts require arguments such as credentials if exploiting an auth vulnerability.
These can be given with the ```--script-args``` switch. An example of this would be used to upload files using the PUT method. This takes two arguments: the URL to upload the file to, and the file's location on disk.  For example:

```nmap -p 80 --script http-put --script-args http-put.url='/dav/shell.php',http-put.file='./shell.php'```

Note that the arguments are separated by commas, and connected to the corresponding script with periods (i.e.  ```<script-name>.<argument>```).

### DNS Zone Transfer
```
nmap --script dns-zone-transfer.nse --script-args dns-zone-transfer.domain= <domain> -p 53 <hosts>
```

### Example of grepping all "Up" IPs from an nmap output file. This can be useful for appending to another file so that only the UP IPs are listed.
```
cat nmap.txt.gnmap | grep -i "Up" | awk '/Up/{print $2}'
```

### Example of scanning a webserver and then piping its output to Nikto for vulnerability scanning
```
nmap -p80,443 <IP>/24 -oG - | nikto.pl -h -
```

### Here are some examples of using Nmap for host vulnerability scanning.

```nmap -Pn --script vuln <target>``` Check for common vulnerabilities.

```nmap -Pn --script exploit <target>``` Scan for vulnerabilities and attempt to automatically exploit them.

```nmap --script dos -Pn <target>``` Test to see if a host is vulnerable to DoS attacks.

```nmap -sV -vv <target>``` Scan and interrogate ports for service version information. Produce very verbose output.
