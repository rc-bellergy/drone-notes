[Configuring C.H.U.C.K. for 18650 Li-ion cell voltage](https://github.com/uavpal/disco-docs/issues/1)

[Disco and batteries](https://github.com/uavpal/disco-docs/wiki/batteries)
Takeoff: 16A
Cruising: 6-8A 

The motor is reported to drop in power around 9.5V: loosing height when turning, slow climbing.
So, I should set the 0% battery to 3.3v (9.9v) for safely.


## Modified Li-ion battery table of
Only BATTERY_PERCENTAGE_TABLE_VOLTAGE changed in the table below:

    #/////////////////////////////////////////////////////////////
    # BATTERY
    BATTERY_FILTER_CO_HZ = 1.0
    VBAT_MIN = 9.7
    VBAT_LOW = 9.8
    VBAT_SHUTDOWN = 9.0
    BATTERY_PERCENTAGE_TABLE_LENGTH = 15
    BATTERY_PERCENTAGE_TABLE_VOLTAGE = 9.05, 9.45, 9.86, 10.09, 10.36, 10.83, 11.14, 11.78, 11.92, 12.01, 12.05, 12.11, 12.15, 12.22, 12.38
    BATTERY_PERCENTAGE_TABLE_PERCENTAGE = 0, 5, 10, 15, 25, 45, 55, 79, 84, 88, 91, 94, 96, 98, 100

Default setting below

    BATTERY_PERCENTAGE_TABLE_VOLTAGE = 9.5, 11.04, 11.11, 11.21, 11.3, 11.4, 11.6, 11.9, 12.02, 12.11, 12.19, 12.26, 12.35, 12.45, 12.5
    BATTERY_PERCENTAGE_TABLE_PERCENTAGE = 0, 5, 10, 15, 25, 45, 55, 79, 84, 88, 91, 94, 96, 98, 100


## Change etc/parameters.conf file

    telnet 192.168.42.1
    mount -o remount,rw /
    vi etc/parameters.conf

    :x


