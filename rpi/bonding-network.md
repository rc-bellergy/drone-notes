# Bonding Network
Idea: How to use two 4G USB modems at same time to provide **more reliable** and **higher speed** network? The **ethernet channel bonding** should be the solution.

## References:
[Main reference](https://blog.wirelessmoves.com/2014/07/ethernet-channel-bonding-with-a-raspberry-pi-and-ubuntu.html)\
I can create the bonding network, but it seems not work. 


[Debian reference](https://wiki.debian.org/Bonding)

[Ubuntu reference](https://help.ubuntu.com/community/UbuntuBonding#Descriptions_of_bonding_modes)

## Install:

    sudo apt-get install ifenslave


## Load the module when kernel start up
 
    sudo pico /etc/modules

    ## Add the line below:
    loop
    lp
    rtc
    bonding

## Modify the `/etc/network/interfaces` file
```conf
# Define slaves   
auto eth0
iface eth0 inet manual
    bond-master bond0
    bond-primary eth0
    bond-mode active-backup

auto wlan0
iface wlan0 inet manual
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
    bond-master bond0
    bond-primary eth0
    bond-mode active-backup

# Define master
auto bond0
iface bond0 inet dhcp
    bond-slaves wlan0
    bond-primary eth0
    bond-mode active-backup
    bond-miimon 100
```

## Enabling systemd-networkd

    sudo systemctl enable systemd-networkd
    sudo reboot now

## Check the status of the bonding driver: 

    cat /proc/net/bonding/bond0 

