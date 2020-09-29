# Start SITL

    cd ~/src/Firmeare
    export DISPLAY=ubuntu-vm:1  (ubuntu-vm:1 is the vncserver screen name)
    export PX4_HOME_LAT=22.3090520
    export PX4_HOME_LON=114.3041529
    HEADLESS=1 make px4_sitl gazebo

Issue: The gazebo didn't sidplay on the VM

    [Err] [RenderEngine.cc:753] Unable to create glx visual

Solution: NOT FIXED yet!


## Install dependencies for Mac OS

    pip install rospkg jinja2
    brew install eigen graphviz libxml2 sdformat3 opencv glib
    brew install gstreamer gst-plugins-base gst-plugins-good
