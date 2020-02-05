# Raspberry Pi

[Nacio+ Raspberry Pi configuration document](https://docs.emlid.com/navio/common/ardupilot/configuring-raspberry-pi/)

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

```
curl -s 'https://raw.githubusercontent.com/zerotier/ZeroTierOne/master/doc/contact%40zerotier.com.gpg' | gpg --import && \
if z=$(curl -s 'https://install.zerotier.com/' | gpg); then echo "$z" | sudo bash; fi
```

### Join ZeroTier
     sudo zerotier-cli join {zerotier-network-id}

## WiFi config file 
> It should be done on the raspi-config. In case you need to modigy the WiFi file directly.
```
sudo pico /etc/wpa_supplicant/wpa_supplicant.conf
```
[Read more...](https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md)


## Start up WiFi
```
sudo ifdown wlan0 && sudo ifup wlan0
```
---

## Show boot log
```
dmesg
```