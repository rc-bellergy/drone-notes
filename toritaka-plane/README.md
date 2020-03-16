# Toritaka Drone Project 2020

This project is to install Pixhawk to Parrot Disco and use a 3G / 4G network to achieve the goal of `long-range ground station control`.

## The Goal
- **Network**
  - [ ] Over 20 km remote control drone over
  - [ ] Bonding two 4G networks to imporive the speed and reliable
  - [x] Using Zerotier setup the virtual LAN to connect ground stations and drones
- **Video**
  - [x] Live streaming FPV vieo
  - [x] Low latency video as low as 50 ms ([use JPEG Stream code](https://github.com/rc-bellergy/pxpi/blob/master/home/pi/jpeg-stream/README.md)) 
  - [x] Remote control on/off video streaming
  - [x] Save video
  - [ ] Save HD video
  - [ ] Remote control start/stop save video
- **Monitoring**
  - [x] Send live drone positions to the Glympse for backup
  - [ ] Send onboard computer upload/download speed to ground station
  - [ ] Sndd 3G/4G network status to ground station
  - [ ] Save cellular network status to flight log

## The Setup
- Body: **Parrot Disco**
- FC: **Pixhawk (FMU V2)**
- Onboard computer: **Raspberry Pi 3**
- Network: **HUAWEI E3372** (3G/4G)
- Firmware: **ArduPlane**

## The source code of onboard computer
https://github.com/rc-bellergy/pxpi

## The Parrot Disco body inside
![Inside the Parrot Disco](images/IMG_4899.jpg)