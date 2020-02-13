# USB Modem

## HUAWEI E3370, E3372, E303c...

### Did the USB loaded
    $ lsusb | grep Huawei
    12d1:1506 Huawei Technologies Co., Ltd. Modem/Networkcard

### Did the E3370 loaded
    $ dmesg | grep 1506
    idVendor=12d1, idProduct=1506, bcdDevice= 1.02

### Install wvdial
    $ sudo apt-get install wvdial

### Edit the wvdial.conf, if need
    $ sudo pico /etc/wvdial.conf

### Test the dial up:

    $ sudo wvdial

### Create the service

    $ sudo pico /etc/systemd/system/wvdial.service
    [Unit]
    Description=wvdial

    [Service]
    ExecStart=/usr/bin/wvdial
    Restart=on-failure
    RestartSec=5

### When the USB modem loaded, call the wvdial.service
    $ sudo pico /udev/rules.d/99-com.rules 
    SUBSYSTEM=="tty", KERNEL=="ttyUSB0", TAG+="systemd", ENV{SYSTEMD_WANTS}+="wvdial.service"

---
## HUAWEI E3372
Plug and Play

---
## A python code check the Huawei HiLink modems for status information 
https://github.com/trick77/huawei-hilink-status