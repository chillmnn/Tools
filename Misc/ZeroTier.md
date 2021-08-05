On the drone device download ZeroTier. This can be done by visiting ZeroTier.com's download page, copy and pasting the curl command to the linux box.

After installing ensure ZeroTier starts with your system run this commnad.
```
sudo systemctl enable zerotier-on
```

Check that everything is functioning.
```
sudo zerotier-cli status
```

On your ZeroTier account create a new network and copy the network ID. Then on the drone input the ID with the following command.
```
sudo zerotier-cli join <NetworkID>
```

To ensure the drone connects to the ZeroTier network on startup enter this.
```
sudo touch /var/lib/zerotier-one.d/<NetworkID>.conf
```

