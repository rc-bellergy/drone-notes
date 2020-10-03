# Simulation
https://dev.px4.io/master/en/simulation/gazebo.html#video

## Build gazebo simulator

    make px4_sitl gazebo

### Issue

    #include <libavcodec/avcodec.h>
    1 error generated.
    ninja: build stopped: subcommand failed.
    FAILED: external/Stamp/sitl_gazebo/sitl_gazebo-build

Is `libavcodec` missing?

### Fix:
Find where is the missing file:

    find / -name avcodec.h

The file 'libavcodec/avcodec.h' is in

    /usr/local/Cellar/ffmpeg/4.3.1_1/include/libavcodec/avcodec.h'

I open the error file and change the include header to 

    #include </usr/local/Cellar/ffmpeg/4.3.1_1/include/avcodec.h>

Not only one file has problem, replace it one by one.

**It is not a good way to handle the error, just work** 

---
## Build jMAVSim simulator 
    cd Firmware
    make px4_sitl jmavsim

### Issue (only on my iMac):
The java version not match.

    Exception in thread "main" java.lang.UnsupportedClassVersionError: me/drton/jmavsim/Simulator has been compiled by a more recent version of the Java Runtime (class file version 58.0), this version of the Java Runtime only recognizes class file versions up to 57.0

### Not fix:
- Update the Java on Mac control panel
- Not work

---

# Set the home location and start a HEADLESS STIL

    cd ~/src/Firmeare

    export PX4_HOME_LAT=22.3090520
    export PX4_HOME_LON=114.3041529
    export PX4_SIM_SPEED_FACTOR=2

    HEADLESS=1 make px4_sitl gazebo_iris

