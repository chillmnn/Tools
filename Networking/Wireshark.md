# Wireshark

### Capture Modes
<b>Promiscuous mode</b> - Sets interface to capture all packets on a network segment to which it is associated to
<b>Monitor mode</b> - Setup the wireless interface to capture all traffic it can receive (Unix/Linux only)

### Capture Filter Syntax
Filter packets during capture
| Syntax  | Protocol | Direction | Host | Value | Logical Operator | Expressions  |
|---------|----------|-----------|------|-------|------------------|--------------|
| Example | TCP      | Src       | IP | 80    | and              | tcp dst IP |

### Display Filter Syntax
Hide packets from a capture display
| Syntax  | Protocol | String1 | String2 | Comparison Operator | Value | Logical Operator | Expressions |
|---------|----------|---------|---------|---------------------|-------|------------------|-------------|
| Example | http     | dest    | IP      | ==                  | IP    | and              | tcp port    |

### Protocol Value
* ether
* fddi
* ip
* arp
* rarp
* decnet
* lat
* sca
* moprc
* mopdl
* tcp
* udp

### Filtering Packets (Display Filters)
| Operator | Discription           | Exmaple                |
|----------|-----------------------|------------------------|
| ```eq``` or ```==``` | Equal                 | ```ip.dest == 192.168.1.1``` |
| ```ne``` or ```!=``` | Not Equal             | ```ip.dest != 192.168.1.1``` |
| ```gt``` or ```>```  | Greater than          | ```frame.len > 10```         |
| ```lt``` or ```<```  | Less than             | ```frame.len <10```          |
| ```ge``` or ```>=``` | Greater than or Equal | ```frame.len >= 10```        |
| ```le``` or ```<=``` | Less than or Equal    | ```frame.len<=10```          |

### Misc.
| Slice Operator      | […] - Range of values |
|---------------------|-----------------------|
| Membership Operator | {} - In               |
| CTRL+E -            | Start/Stop Capturing  |

### Logical Operators
| Operator  | Description        | Example                                                                      |
|-----------|--------------------|------------------------------------------------------------------------------|
| ```and``` or ```&&``` | Logical AND        | All the conditions should match                                              |
| ```or``` | Logical OR         | Either all or one of the condition should match                              |
| ```xor``` or ```^^``` | Logical XOR        | exclusive alternation – Only one of the two conditions should match not both |
| ```not``` or ```!```  | NOT(Negation)      | Not equal to                                                                 |
| ```[n]``` ```[…]```   | Substring operator | Filter a specific word or text                                               |


### Common Filtering Commands
| Usage                  | Filter Syntax                                       |
|-----------------------------------------|----------------------------------------------------------------|
| Wireshark Filter by IP                  | ```ip.addr == 10.10.50.1```                                          |
| Filter by Destination IP                | ```ip.dest == 10.10.50.1```                                          |
| Filter by Source IP                     | ```ip.src == 10.10.50.1```                                           |
| Filter by IP range                      | ```ip.addr >= 10.10.50.1 and ip.addr <= 10.10.50.100```              |
| Filter by Multiple Ips                  | ```ip.addr == 10.10.50.1 and ip.addr == 10.10.50.100```              |
| Filter out/ Exclude IP address          | ```!(ip.addr == 10.10.50.1)```                                       |
| Filter IP subnet                        | ```ip.addr == 10.10.50.1/24```                                       |
| Filter by multiple specified IP subnets | ```ip.addr == 10.10.50.1/24 and ip.addr == 10.10.51.1/24```          |
| Filter by Protocol                      | dns http ftp ssh arp telnet icmp                               |
| Filter by port (TCP)                    | ```tcp.port == 25```                                                 |
| Filter by destination port (TCP)        | ```tcp.dstport == 23```                                              |
| Filter by ip address and port           | ```ip.addr == 10.10.50.1 and Tcp.port == 25```                       |
| Filter by URL                           | ```http.host == “host name”```                                       |
| Filter by time stamp                    | ```frame.time >= “June 02, 2019 18:04:00”```                         |
| Filter SYN flag                         | ```tcp.flags.syn == 1```   ```tcp.flags.syn == 1 and tcp.flags.ack == 0``` |
| Wireshark Beacon Filter                 | ```wlan.fc.type_subtype = 0x08```                                    |
| Wireshark broadcast filter              | ```eth.dst == ff:ff:ff:ff:ff:ff```                                   |
| WiresharkMulticast filter               | ```(eth.dst[0] & 1)```                                               |
| Host name filter                        | ```ip.host = hostname```                                             |
| MAC address filter                      | ```eth.addr == 00:70:f4:23:18:c4```                                  |
| RST flag filter                         | ```tcp.flags.reset == 1```                                           |

