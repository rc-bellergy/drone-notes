# PX4 Development
[Development Guide]()

---
## Development Environment on Mac
https://dev.px4.io/v1.9.0/en/setup/dev_env_mac.html

### Install steps:

    brew tap PX4/px4

    # fix the "Formulae found in multiple taps" issue
    brew untap ardupilot/px4
    brew tap --repair
    brew update

    brew install px4/px4/px4-dev

    brew install px4-sim

[Install log](install.log)

### Clone the frameware source code:
https://dev.px4.io/v1.9.0/en/setup/building_px4.html

    git clone https://github.com/rc-bellergy/Firmware

---
## Simulation
[Simulation Guide](https://github.com/PX4/Devguide/tree/master/en/simulation)

### How to build and start jmavsim in the remove server and receive the MAVLink (e.g. QGrountcontrol) in the local PC?

Do following steps in the remote server:

1. Build `px4_sitl` and start `jmavsim`\
    ```HEADLESS=1 make px4_sitl jmavsim```

2. Install the [mavlink-router](https://github.com/intel/mavlink-router)

3. Start `mavlink-router` route the data to your local PC\
   ```/usr/bin/mavlink-routerd 127.0.0.1:14550 -e 192.168.192.101:14550```


### Build the SITL plane in gazebo
https://dev.px4.io/v1.9.0/en/simulation/gazebo.html
https://github.com/PX4/sitl_gazebo

#### Install gazebo: 

    sudo apt-get install gazebo9

> Note: Debian has debian7 in stable package (2020-01-08)\
> Installing debian9, you have to change the package repo to `buster`\
> 
> https://packages.debian.org/buster/gazebo9\

```
export PX4_HOME_LAT=22.305500
export PX4_HOME_LON=114.299520
export PX4_HOME_ALT=110
HEADLESS=1 make px4_sitl gazebo_plane
```

> Note: If you got error:  FAILED: include/moc_gazebo_video_stream_widget.cpp 
> Go here <Firmware>/Tools/sitl_gazebo/CMakeLists.txt
> And trun off the gstreamer plugin 
> option(BUILD_GSTREAMER_PLUGIN "enable gstreamer plugin" "OFF")
> make clean

> Config the plane: 
> Firmware/Tools/sitl_gazebo/models/plane/plane.sdf


### HITL
http://dev.px4.io/v1.9.0/en/simulation/hitl.html


### Build Pixhawk 1
    make px4_fmu-v2_default

> There is issue run on Mac. Only works on the Linux.

### Craete Digital Elevation Models
http://gazebosim.org/tutorials?tut=dem&cat=build_world#HowdoIgetaDEMfileofmyregionofinterest?

    