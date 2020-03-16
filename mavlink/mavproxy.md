# MAVProxy [**NOT IN USE**]

[Install MAVProxy](https://ardupilot.github.io/MAVProxy/html/getting_started/download_and_installation.html#mac)

    sudo pip3 install wxPython
    sudo pip3 install gnureadline
    sudo pip3 install billiard
    sudo pip3 install numpy pyparsing
    sudo pip3 install MAVProxy

> Since the MAVProxy used high CPU and dose not support PX4. I changed to use mavlink-router. 

### Update /etc/rc.local to start the mavproxy when boot
```sh
# Start MAVProxy
(
echo "Start MAVProxy" $(date)
echo "sudo screen -r mavproxy to open the screen"
cd /home/bellergy/
screen -dmS mavproxy \
/usr/local/bin/mavproxy.py --non-interactive --daemon --aircraft pxpi --master=/dev/ttyAMA0 --baudrate 115200 --out=udpbcast:192.168.192.255:14550 --out=udp:127.0.0.1:14550
) >> /tmp/rc.log 2>&1
```
> Raspberry Pi 2 set `--master=/dev/ttyAMA0`<br>
> Raspberry Pi 3 (Bluetooth enable) set `--master=/dev/ttyS0`