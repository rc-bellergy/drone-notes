# Install and run MAVSDK on Raspberry Pi

I use MAVSDK to implement the offboard control functions. There is the note of installation.

## Install `mavsdk` for Python3 (mavsdk only support Python 3)

    pip3 install mavsdk

---
## Issue: 
In Raspberry Pi, the `pip3 install mavsdk` didn't install `mavsdk_server`, you will need to get and run the `mavsdk_server` binary manually. (but why!? I don't know!)

## Soulation:
Download the `mavsdk_server` for RPi here.

You can find binary for Raspberry Pi version in [here](https://github.com/mavlink/mavsdk/releases).

    wget https://github.com/mavlink/MAVSDK/releases/download/v0.31.0/mavsdk_server_linux-armv6

Move it to ~/MAVSDK-Python/mavsdk/bin/

    cp mavsdk_server_linux-armv6 ~/MAVSDK-Python/mavsdk/bin/mavsdk_server
    cd ~/MAVSDK-Python/mavsdk/bin/
    chmod u+x mavsdk_server
---

## Start the mavlink-router
In my setup, the `/dev/serial0` connected to mavlink-router, I can't connect it to `mavsdk_server`.

So, I setup the mavlink-router forwards the mavlink to 127.0.0.1:14550, then the `mavsdk_server` can connect to here.

    /usr/bin/mavlink-routerd 127.0.0.1:14550 -e 127.0.0.1:14550

## Start the mavsdk_server

    ~/MAVSDK-Python/mavsdk/bin/mavsdk_server udp://127.0.0.1:14550 -p 5000   

## A sample python script to connet the drone
Following code connect the find the `mavsdk_server` on `localhost` port `5000` and connect the drone on `udp://127.0.0.1:14550`
```python
drone = System(mavsdk_server_address='localhost', port="5000")
await drone.connect(system_address="udp://127.0.0.1:14550")
```