# Using iPhone to connect the drone with the ground station

## Idea
Why don't use a iPhone SE (113 g) to replace Raspberry Pi (23 g), 4G USB (35 g) and camera (3 g)?

## Why?
- Better connection?
- Better reconnect?
- Independent battery ＋ Find My iPhone feature
- Use Youtube, FB live as monitor camera?
- Connect 360 camera + live streaming

## How?
- Ground Station connect iPhone (use 4G network + ZeroTier)
- iPhone connect flight controller use [bluetooth](http://ardupilot.org/copter/docs/common-mission-planner-bluetooth-connectivity.html)


## References:
[MAVProxy Wifi Bridge](https://ardupilot.github.io/MAVProxy/html/getting_started/mavbridge.html#mavproxy-wifi-bridge)

[SwiftSocket](https://github.com/swiftsocket/SwiftSocket)