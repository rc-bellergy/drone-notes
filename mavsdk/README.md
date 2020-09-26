# Install and run MAVSDK on Raspberry Pi

I use MAVSDK to implement the offboard control functions. There is the note of installation.

## Install `mavsdk` for Python3 (mavsdk only support Python 3)

    pip3 install mavsdk

---
## Issue: You will need to get and run the 'mavsdk_server' binary manually

## Soulation:

### Download `mavsdk_server`

The pip3 install mavsdk didn't download mavsdk_server, we need to download it here.\
Please find the update version in https://github.com/mavlink/mavsdk/releases. The `mavsdk_server_linux-armv6
24` works on Raspberry Pi.

    wget https://github.com/mavlink/MAVSDK/releases/download/v0.31.0/mavsdk_server_linux-armv6

    chmod u+x avsdk_server_linux-armv6
---


## Start the mavsdk_server

    ./mavsdk_server_linux-armv6 -p 50051


## Start the mavlink-router

    /usr/bin/mavlink-routerd -e 192.168.192.101:14550 -e 127.0.0.1:14550 -e 127.0.0.1:14540

The mavsdk_server default waiting the drone (system) mavlink on 14540 port. I use mavlink-router to route mavlink to the port. 

The sample below, `127.0.0.1:14550` is the default mavlink out port,\
`-e 192.168.192.101:14550` route to ground station\
`-e 127.0.0.1:14540 route` to offboard MAVSDK server

   mavlink-routerd -e 192.168.192.101:14550 -e 127.0.0.1:14540 127.0.0.1:14550
