# Drone Daemon (Ideas)
A background running program loaded on the RPi starts up. It can provide the following services:
- Start/stop Mavproxy by remote control
- Start/stop video streaming by remote control
- Start/stop video recording by remote control or drone arm/disarm
- Send GPD data to Glympse when drone armed
- Send Glympse share link to Pushbullet

## Send GPS data to Glympse
[x] It can submit the drone location to Glympse when flying.

## Send Glympse share link to Pushbullet
[x] IWhen RPi craeted a Glympse sccount, it will send a share link to Pushbullet. The user can use the link to open the Glympse app and monitor the drone location.

## Submit the drone location to Glympse every 5 sec.
[x] When the drone **Armed** and **GPS Fix** the program will start to submit the drone location to Glympse every 5 sec.

## Start/stop the Mavproxy by remote control
Start the Mavproxy when RPi booted.<br>
Monitor the remote control input to start or stop the Mavproxy.

## Start/stop the video streaming by remote control
[x] The program will monitor the remote control input to start or stop the video streaming.
- 

https://github.com/rc-bellergy/glympse