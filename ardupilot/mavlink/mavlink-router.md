# mavlink-router
Use [mavlink-router](https://github.com/intel/mavlink-router) to replace the mavproxy because the mavproxy dose not support px4.

## Install

### Git clone
    git clone https://github.com/intel/mavlink-router.git
    cd mavlink-router
    git submodule update --init --recursive

### Config
    ./autogen.sh && ./configure CFLAGS='-g -O2' \
        --sysconfdir=/etc --localstatedir=/var --libdir=/usr/lib64 \
    --prefix=/usr
> There are some warning echo but still works

### Make
    make
    make install

> If show `ImportError: No module named 'future'` when make;<br>
> Install it `pip3 install future`<br>
> If no `pip3`;<br>
> Install it `sudo apt-get install python3-pip`

## Create a config file
    sudo mkdir /etc/mavlink-router
    sudo pico main.conf

> [config file reference](https://github.com/intel/mavlink-router/blob/master/examples/config.sample)

## Run

    mavlink-routerd /dev/ttyAMA0:57600 -e 192.168.192.101:14550

## Issue
