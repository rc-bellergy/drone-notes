# Q&A

## I can connect but get random characters
Set the baudrate to 57600 (921600 not work, too fast?)

---
## WARNING: You should uninstall ModemManager as it conflicts with APM and Pixhawk
Uninstalled `modemManager`, no side effect so far.

---
##  What happen when connect both Radio and Joystick? **QGroundcontrol**
Joystick will overrided Radio<br>
If the joystick lost connection, the radio control will take over.

---
##  How to get Radio/Joystick actions in RPi?
Use DroneKit

---
##  How to send action from RC > RPI > FC?

---
##  How to send GPS loctaion to Glympse?
[There is my glympse.py code](https://github.com/rc-bellergy/glympse.git)

---
##  How to get 4G signal status and send to Ground Station?<br>

---
##  Why there is noise echo in the mavpython connect px4?<br>
[MAVProxy not compatible with PX4](https://discuss.px4.io/t/mavproxy-not-compatible-with-px4/7164/2). So that shell I use px4?

---
## If the MAVProxy no compatible with PX4, can MAVSDK-Python do same thing as MAVProxy?
### Install (Under Testing)
[MAVSDK-Python project](https://github.com/mavlink/MAVSDK-Python)

#### Install python3
    sudo apt install python3-pip

#### Install MAVSDK-Python
    sudo pip3 install mavsdk    
