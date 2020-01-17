# Parrot Disco over 4G/LTE (softmod)
    https://github.com/uavpal/disco4g#parrot-disco-over-4glte-softmod 

## Install
    https://github.com/uavpal/disco4g/wiki/Installation

## Check versions
    https://github.com/uavpal/disco4g/blob/master/README.md#supportedhw
    Parrot Skycontroller 2, Firmware 1.0.9
    Parrot Disco, Firmware 1.7.1
    Linux BellergyDISCO 3.4.11+ #1 SMP PREEMPT armv7l GNU/Linux
    pppd version 2.4.6

## Support 4G USB
    HUAWEI E3372


## 4G USB LED message
    Green, flashing twice every 2s: The USB-Modem is powered on.
    Green, flashing once every 0.2s: The software of the USB-Modem is being upgraded.
    Green, flashing once every 2s: The USB-Modem is registering with a 2G network.
    Cyan, flashing once every 2s: The USB-Modem is registering with a 3G/3G+network.
    Blue, flashing once every 2s: The USB-Modem is registering with a 4G network.
    Green, solid: The USB-Modem is connected to a 2G network.
    Cyan, solid: The USB-Modem is connected to a 3G/3G+ network.
    Blue, solid: The USB-Modem is connected to a 4G network.

## Detail of using 4G USB to access internet
    Raspberry Pi 用 3G 網卡(3G USB dongle)上網
    https://www.raspberrypi.com.tw/771/how-to-setup-a-usb-3g-modem-on-raspberry-pi/

## Glympse Location Shareing
    https://developer.glympse.com/account/apps
    API key: 0o4kheKQk95UtyKsJnto

## Pushbullet
    https://www.pushbullet.com/
    Account: michael@designquest.com.hk Google Login
    Token: o.8wRiGgA35DDAYfLRX6OOyVmggwqU80VW

## ZeroTier
    https://my.zerotier.com/
    Account: michael@designquest.com.hk Google Login
    Network ID: d3ecf5726d264851

## Slack
    https://uavpal.slack.com/messages/C6TCG655E/

## Install
    telnet 192.168.42.1
    mv /data/ftp/internal_000/disco4g-* /tmp/disco4g
    chmod +x /tmp/disco4g/*/*_install.sh
    /tmp/disco4g/disco/disco_install.sh
    /tmp/disco4g/skycontroller2/skycontroller2_install.sh
    reboot

## Debug
There is a success connect 4G dmesg print out:
```
dmesg
[   16.532789] option 1-1.2:1.0: GSM modem (1-port) converter detected
[   16.546263] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB0
[   16.546647] option 1-1.2:1.1: GSM modem (1-port) converter detected
[   16.546879] usb 1-1.2: GSM modem (1-port) converter now attached to ttyUSB1
[   16.547561] scsi1 : usb-storage 1-1.2:1.3
[   16.548501] scsi2 : usb-storage 1-1.2:1.4
[   17.552948] scsi 2:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[   17.560458] scsi 1:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   17.593589] sd 2:0:0:0: [sda] Attached SCSI removable disk
[   17.672142] PPP generic driver version 2.4.2
[   17.771701] PPP Deflate Compression module registered
[   17.808507] PPP BSD Compression module registered
```

## Check Log of uavpal_disco
    ulogcat -d | grep 'uavpal_disco'

## Start Up 
    When the Linux (C.H.U.C.K.) start, script below will run:
    /data/ftp/uavpal/conf/70-huawei-e3372.rules

    If the Huawei USB device (idVendor:12d1) be found, script below will run:
    /data/ftp/uavpal/bin/uavpal_disco.sh

## Limiting Disco video streaming bandwidth
    https://github.com/mainframe/disco4g/tree/master/Disco#optional-limiting-disco-video-streaming-bandwidth
    
    telnet 192.168.42.1
    cp -p /usr/bin/DragonStarter.sh /data/ftp/internal_000/backup/DragonStarter.sh
    BW_LIMIT="1800"
    mount -o remount,rw /
    sed -i.bak "s/^DEFAULT_PROG=.*/DEFAULT_PROG=\"usr\/bin\/dragon-prog -q $BW_LIMIT\"/g" /usr/bin/DragonStarter.sh
    mount -o remount,ro /
    reboot

## Battery Mod
    https://github.com/uavpal/disco-docs/wiki/batteries


## Connect ZeroTier
    sudo zerotier-cli join d3ecf5726d264851

## My Q&A

1. What is the APN?<br>
    I'm using Smartone, but the APN name should be 'internet' NOT 'smartone'

2. Can


---

## Background Information

### BusyBox
C.H.U.C.K.'s shell
https://zh.wikipedia.org/wiki/BusyBox

### 
https://www.rsaconference.com/writable/presentations/file_upload/mbs-w14-parrot-drones-hijacking.pdf


