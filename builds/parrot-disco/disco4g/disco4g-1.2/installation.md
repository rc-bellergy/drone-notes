Please go to https://github.com/uavpal/disco4g/wiki/Installation for detailed instructions.

1. Copy following folder from old version:
    - disco/uavpal/conf/*
    - skycontroller2/uavpal/conf/*
2. Connect your PC's Wi-Fi to the Disco
3. FTP to 192.168.42.1
4. Set the transfer type to Binary
5. Transfer the disco4g-1.2 to the "/internal_000" folder on the Disco
6. Double press the Disco's power button to enable the telnet server
7. telnet 192.168.42.1
```
mv /data/ftp/internal_000/disco4g-* /tmp/disco4g
chmod +x /tmp/disco4g/*/*_install.sh
/tmp/disco4g/disco/disco_install.sh
/tmp/disco4g/skycontroller2/skycontroller2_install.sh
reboot
```
