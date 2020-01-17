# DroneKit

[Quick Start](https://dronekit-python.readthedocs.io/en/latest/guide/quick_start.html)

[DroneKit-SITL Server](/web-hosting/accounts/designquest.dq@gmail.com/drone-server.md)

## Start DroneKit SITL with MAVProxy
https://dronekit-python.readthedocs.io/en/latest/develop/sitl_setup.html

### Start SITL
    dronekit-sitl copter-3.3 --home=22.317990, 114.200653,10,0

### Start MAVProxy
    mavproxy.py --master tcp:127.0.0.1:5760 --out=udp:192.168.192.103:14550 --out=udp:127.0.0.1:14550 --aircraft sitl
> 192.168.192.103 is ZeroTier IP to my office iMac
> 127.0.0.1 is for local DroneKit connect
