# Network

# WiFi config file

    /etc/wpa_supplicant/wpa_supplicant.conf

# Restart the WiFi

    sudo sudo ifconfig wlan0 down && sudo ifconfig wlan0 up

# Close the USB modam network

    sudo ifconfig eth0 down

# Zerotier
[Help/support site](https://zerotier.atlassian.net/wiki/discover/all-updates)

# Set the priority of network connections

### Check the priority
Use `route` to check the priority of networks. In the sample below, the lower **Metric** **eth0** will be used.
    
    route -n

    Destination  Gateway     Genmask  Flags Metric Ref  Use Iface
    0.0.0.0      10.42.0.2   0.0.0.0  UG    200    0    0   wlan0
    0.0.0.0      10.42.0.1   0.0.0.0  UG    100    0    0   eth0

### Change the priority
The solution not found because the networks are behind the `zerotier`. Changing the `Metric` did not work. The first priority alwary is `zerotier`. The question should be "How to change the priority of network connections of ZeroTier?"

---