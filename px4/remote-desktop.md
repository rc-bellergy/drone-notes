# Install Remote Desktop to Ubuntu on GCE
https://subscription.packtpub.com/book/big_data_and_business_intelligence/9781788474221/1/ch01lvl1sec15/installing-and-configuring-ubuntu-desktop-for-google-cloud-platform

Create a Ubuntu 18 on Google Compute Engine, then install:

# Install Ubuntu Gnome Desktop

    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get install gnome-shell
    sudo apt-get install ubuntu-gnome-desktop
    sudo apt-get install autocutsel
    sudo apt-get install gnome-core
    sudo apt-get install gnome-panel
    sudo apt-get install gnome-themes-standard

# Install the VNC Server

    sudo apt-get install tightvncserver
    touch ~/.Xresources
    tightvncserver
    pico /home/travmix/.vnc/xstartup

## update the xstartup file
    #!/bin/sh

    autocutsel -fork
    xrdb $HOME/.Xresources
    xsetroot -solid grey
    export XKL_XMODMAP_DISABLE=1
    export XDG_CURRENT_DESKTOP="GNOME-Flashback:Unity"
    export XDG_MENU_PREFIX="gnome-flashback-"
    unset DBUS_SESSION_BUS_ADDRESS
    gnome-session --session=gnome-flashback-metacity --disable-acceleration-check --debug &

## Kill the vnc server

    vncserver -kill :1

# Start the VNC Server

    vncserver -geometry 1024x640


# Connect from Mac

    ssh -L 5901:localhost:5901 travmix.com