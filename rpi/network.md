# Network

# WiFi config file
    /etc/wpa_supplicant/wpa_supplicant.conf

# Restart the WiFi
    sudo sudo ifconfig wlan0 down && sudo ifconfig wlan0 up

# Close the USB modam network
    sudo ifconfig eth0 down

# Zerotier
[Help/support site](https://zerotier.atlassian.net/wiki/discover/all-updates)


# WiFi network tools
[Reference](https://www.cyberciti.biz/tips/linux-find-out-wireless-network-speed-signal-strength.html)
## Scan WiFi
    sudo iwlist wlan0 scanning | grep ESSID

## Show connected WiFi info
    iwconfig wlan0

## Monitor the WiFi quality
    watch -n 1 cat /proc/net/wireless

## Show ZeroTier network status (zt2lrwgvd2)
    sudo iftop -n -i zt2lrwgvd2

