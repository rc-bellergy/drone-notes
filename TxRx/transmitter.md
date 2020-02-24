# Fixed Wing, Pixhawk and Transmitter

## Connecting the receiver using X8R S.Bus
![X8R wiring](http://ardupilot.org/plane/_images/RCIN_connection.jpg)

## FrSky Taranis X9D Plus
Make sure installed [OpenTX](http://www.open-tx.org/downloads.html) firmware (2.2.1/2.2.2).
![Taranis X9D Plus](http://ardupilot.org/plane/_images/FrSky_Taranis9XD_Plus.jpg)

## FrSky telemetry
the Taranis is that it can receive and display telemetry data directly from ArduPilot and on-board FrSky telemetry sensors, such as flight mode, GPS status, current drawn and cell voltages, and even ArduPilot messages, that can be added to your vehicle.

ArduPilot has FrSky telemetry drivers to natively output flight controller information through the serial ports. 

![wiring](http://ardupilot.org/plane/_images/FrSky_Conn_Phawk-X8R.jpg)

[Setup](http://ardupilot.org/plane/docs/common-frsky-telemetry.html#common-frsky-telemetry)
- FrSky Taranis X9D
- X8R
- A telemetry cable (custom build)
- FrSky FLVSS (optional)

[The custom build the telemetry cable](https://discuss.ardupilot.org/t/some-soldering-required/27613)
![](https://discuss.ardupilot.org/uploads/default/optimized/2X/2/25a0d6363a7f6330d9e21b74ab4c0bec4c88fd62_1_690x459.jpg)

[Yaapu Frsky Telemetru Script](https://github.com/yaapu/FrskyTelemetryScript)

[How RS-232 to TTL works?](https://www.sparkfun.com/tutorials/215)

## Issue
The telemetry works perfectly until arming the motor, then the telemetry apparently do not receive anymore data from Pixhawk.
[Fixed:  Once changed with other quality SD cards the Frsky native telemetry work again even after arming](https://discuss.ardupilot.org/t/solved-bug-with-frsky-native-telemetry-arming-disable-it/21789)
