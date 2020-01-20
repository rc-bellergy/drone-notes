# Raspberry Pi

[Nacio+ Raspberry Pi configuration document](https://docs.emlid.com/navio/common/ardupilot/configuring-raspberry-pi/)

## Restore SD card image
```
diskutil list                           // show the SD card disk path
diskutil unmountDisk /dev/{diskx}       // unmount SD card
sudo newfs_msdos -F 16 /dev/{diskx}     // format SD card
sudo dd if={/path/of/image/xxx.dmg} of=/dev/{diskx}    // restore image file to SD card
```

## Backup SD card image
```
diskutil list
sudo dd if=/dev/{diskx} of=~{/path/of/image/xxxx.dmg}
```
---

## If the SD card is too large for backup?
[Read here...](https://www.raspberrypi.org/forums/viewtopic.php?t=60161#p450676)


## Login default username and password
```
default user: pi
default password: raspberry
```

## Expanding disk space
```
sudo raspi-config --expand-rootfs
```

## Security Setup
[Document](https://www.raspberrypi.org/documentation/configuration/security.md)

### Generate SSH Key and copy to RPI
> In your Mac

     ssh-keygen -t rsa -f ~/.ssh/[KEY_FILE_NAME] -C [USERNAME]
     chmod 400 ~/.ssh/[KEY_FILE_NAME]
     cat ~/.ssh/[KEY_FILE_NAME].pub | ssh [USERNAME]@[IP-ADDRESS] 'mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys'

## Respi config
```
sudo raspi-config
```

## Install ZeroTier

     curl -s 'https://raw.githubusercontent.com/zerotier/ZeroTierOne/master/doc/contact%40zerotier.com.gpg' | gpg --import && \
     if z=$(curl -s 'https://install.zerotier.com/' | gpg); then echo "$z" | sudo bash; fi

## WiFi config file 
> It should be done on the raspi-config. In case you need to modigy the WiFi file directly.
```
sudo pico /etc/wpa_supplicant/wpa_supplicant.conf
```
[Read more...](https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md)

## Home router info, add it to wpa_supplicant.conf
```
network={
     ssid="Bellergy 2.4G"
     psk="dodo6162"
     key_mgmt=WPA-PSK
     id_str="home-1F"
}
network={
     ssid="Dollergy 2.4G"
     psk="dodo6162"
     key_mgmt=WPA-PSK
     id_str="home-2F"
}
network={
     ssid="DQ-Network"
     psk="Z4=d6n7N"
     key_mgmt=WPA-PSK
     id_str="office"
}
network={
     ssid="Bellergy iPhone"
     psk="jk6162jk"
     key_mgmt=WPA-PSK
     id_str="my-iphone-hostspot"
}
```

## Start up WiFi
```
sudo ifdown wlan0 && sudo ifup wlan0
```
---

## Show boot log
```
dmesg
```

## Show started service
     service --status-all

## Show Network Bandwidth
Install iftop
```
sudo apt-get install iftop
```
Look up network interface ofcat  ZeroTier
```
ip link show
```
Show ZeroTier network status (zt2lrwgvd2)
```
sudo iftop -n -i zt2lrwgvd2

```

## Set the priority of networks
http://0pointer.de/lennart/projects/ifmetric/
Install ifmetric
```
sudo apt-get install ifmetric
```

## Show Joined WiFi
```
iwgetid
```


[Read more...](https://superuser.com/questions/331720/how-do-i-set-the-priority-of-network-connections-in-ubuntu)

