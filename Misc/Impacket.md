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
