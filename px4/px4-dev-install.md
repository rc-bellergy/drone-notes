# Development Environment on **Ubuntu LTS**

https://dev.px4.io/master/en/setup/dev_env_linux_ubuntu.html

    wget https://raw.githubusercontent.com/PX4/Firmware/master/Tools/setup/ubuntu.sh

    wget https://raw.githubusercontent.com/PX4/Firmware/master/Tools/setup/requirements.txt

    source ubuntu.sh

    git clone https://github.com/PX4/Firmware.git --recursive

    ./Tools/setup/ubuntu.sh

# Building PX4 Software

https://dev.px4.io/master/en/setup/building_px4.html

    cd ~/src/Firmeare
    export DISPLAY=ubuntu-vm:1  (ubuntu-vm:1 is the vncserver screen name)
    export PX4_HOME_LAT=22.3090520
    export PX4_HOME_LON=114.3041529
    make px4_sitl gazebo

Issue: The gazebo didn't sidplay on the VM

    [Err] [RenderEngine.cc:753] Unable to create glx visual

Solution: NOT FIXED yet!

# Install mavlink-router

    git clone https://github.com/intel/mavlink-router.git
    cd mavlink-router
    git submodule update --init --recursive
    sudo apt install python-future
    sudo apt install python3-future
    sudo apt install libtool
    sudo apt install autoconf
    ./autogen.sh && ./configure CFLAGS='-g -O2' \
    --sysconfdir=/etc --localstatedir=/var --libdir=/usr/lib64 \
    --prefix=/usr
    make
    sudo make install

## Start the mavlink-router

    mavlink-routerd -e 192.168.192.101:14550 127.0.0.1:14550

Issue: QGroundcontrol `Communication Lost` when `Armed`

Solution: change `SDLOG_MODE` to disable