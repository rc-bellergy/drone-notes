# Bonding Network
Idea: How to use two 4G USB modems at same time to provide **more reliable** and **higher speed** network? The **ethernet channel bonding** should be the solution.

## References:
[Debian reference - ](https://wiki.debian.org/Bonding)\
I'm following this reference.

[Linux reference - Very detail](https://wiki.linuxfoundation.org/networking/bonding)

[Shall I study the Ethernet Interface first?](https://wiki.debian.org/NetworkConfiguration#Setting_up_an_Ethernet_Interface)

[Ubuntu reference - NOT for Debian](https://help.ubuntu.com/community/UbuntuBonding#Descriptions_of_bonding_modes)

## Install:

    sudo apt-get install ifenslave


## Load the module when kernel start up
 
    sudo pico /etc/modules

    ## Add the line below:
    bonding

## Modify the `/etc/network/interfaces` file
```conf
[TODO: copy the config file to here when testing successed.]

```

## Enabling systemd-networkd

    sudo systemctl enable systemd-networkd
    sudo reboot now

## Check the status of the bonding driver: 

    cat /proc/net/bonding/bond0

    Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)

    Bonding Mode: fault-tolerance (active-backup)
    Primary Slave: eth0 (primary_reselect always)
    Currently Active Slave: eth0
    MII Status: up
    MII Polling Interval (ms): 100
    Up Delay (ms): 0
    Down Delay (ms): 0

    Slave Interface: eth0
    MII Status: up
    Speed: Unknown
    Duplex: Unknown
    Link Failure Count: 0
    Permanent HW addr: 0c:5b:8f:27:9a:64
    Slave queue ID: 0

    Slave Interface: wlan0
    MII Status: up
    Speed: Unknown
    Duplex: Unknown
    Link Failure Count: 1
    Permanent HW addr: b8:27:eb:e9:f9:b7
    Slave queue ID: 0

## Check route, it should show `bond0` and `zt2lrwgvd2` only
    route -n

    Destination    Gateway      Genmask        Flags Metric Ref Use Iface
    0.0.0.0        192.168.8.1  0.0.0.0        UG    0      0     0 bond0
    192.168.8.0    0.0.0.0      255.255.255.0  U     0      0     0 bond0
    192.168.192.0  0.0.0.0      255.255.255.0  U     0      0     0 zt2lrwgvd2

## Testing

    