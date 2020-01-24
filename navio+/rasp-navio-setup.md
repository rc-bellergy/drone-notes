# NAVIO

## Documents
[Navio+ Offical Document](https://docs.emlid.com/navio/)

---
## Setup
Setup Respberry Pi please read [rpi basic setup](../rpi/basic-setup.md)

[ArduPilot installation and running](https://docs.emlid.com/navio/common/ardupilot/installation-and-running/)

---

## SSH Login
```
ssh bellergy@navio.local
user: bellergy
```
 
## Update arduplane firmware here:
http://firmware.ardupilot.org/Plane/stable/navio/
```
sudo curl http://firmware.ardupilot.org/Plane/stable/navio/arduplane -o /opt/ardupilot/navio/arduplane-3.8/bin/arduplane
sudo chmod 775 arduplane
```

### Enable ZeroTear service and join NAVIO nwtrowk
    sudo systemctl status zerotier-one.service
    sudo zerotier-cli join 1c33c1ced0a29aaa

## [Mavlink connection setup](https://docs.emlid.com/navio/common/ardupilot/installation-and-running/#specifying-launching-options)

    sudo nano /etc/default/arduplane
    // Boardcast to all IPs:
    TELEM1="-A udp:192.168.192.255:14550:bcast"

    sudo nano /etc/systemd/system/arduplane.service
    // The arduplane.service started before Zerotier's IP setup. Add 10 second delay to the arduplane.service, wait Zerotier ready.
    [Service]
    ExecStartPre=/bin/sleep 10

Restart
```
sudo systemctl daemon-reload
sudo systemctl stop arduplane
sudo systemctl start arduplane
```


---

## [systemd](https://wiki.archlinux.org/index.php/Systemd)
由於 arduplane.service 要等待 zerotier-one.service 完成後提供IP，才能把 data 回傳給 ground station。了解 systemd 是重要的步驟，以安排 services 開啟的次序和相關性。

The unit files are here:
```
/etc/systemd/system/*
/etc/systemd/system/arduplane.service
/etc/systemd/system/multi-user.target.wants/zerotier-one.service
/etc/systemd/system/raspicam.service
```

Add following lines to arduplane.service under [Unit], wait network ready to strat up
```
After=network-online.target
Wants=network-online.target
```

For debug, show systemd stratup log
```
sudo journalctl -u arduplane
sudo journalctl -u zerotier-one
sudo journalctl -u raspicam
```

---

## [Video Streaming](../rpi/video-streaming.md)

---

## Install Huawei E3372 USB Modem
Plug and play! :-)

---
