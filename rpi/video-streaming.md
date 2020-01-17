# Video Streaming

## [Video Streaming](https://docs.emlid.com/navio/common/dev/video-streaming/)
Raspbarry Pi video streaming start up script:
- [raspivid](https://www.raspberrypi.org/documentation/usage/camera/raspicam/raspivid.md) is the command line tool for capturing video with the camera module of Raspbarry Pi
- [gst-launch-1.0](https://gstreamer.freedesktop.org/documentation/tools/gst-launch.html) build and run a GStreamer pipeline
- [Gstreamer basic real time streaming tutorial](http://www.einarsundgren.se/gstreamer-basic-real-time-streaming-tutorial/)

### Install gstreamer1.0
    sudo apt-get update
    sudo apt-get install gstreamer1.0-tools gstreamer1.0-plugins-good gstreamer1.0-plugins-bad

### Start vieo streaming script
    raspivid -n -w 1280 -h 720 -b 1000000 -fps 15 -t 0 -o - | gst-launch-1.0 -v fdsrc ! h264parse ! rtph264pay config-interval=10 pt=96 ! udpsink host=192.168.192.101 port=5600

> The 192.168.192.101 is remote server IP


#### Remarks of raspivid options
| Options        | Descriptions                                 |
| -------------- | -------------------------------------------- |
| -n             | No preview window                            |
| -b             | bitrate (1000000 = 10Mbits/s)                |
| -t 0           | timeout 0 = run continuously                 |
| -o -           | output file '-' all output is sent to stdout |
| -vs            | Turn on video stabilisation                  |
| -ex auto/night | Exposure auto or night mode                  |
| -drc high      | Increasing the range of dark areas,          |
|                | and decreasing the brighter areas            |

Adjust bitrate with -b switch or -fps if your video lags behind.

---
```
gst-launch-1.0  
-v          Output status information (do I need it?)
fdsrc       source from unix file descriptor
h264parse
rtph264pay config-interval=10 pt=96
udpsink host=192.168.192.101                
```

## Autostarting on boot
### [Reference](https://docs.emlid.com/navio/common/dev/video-streaming/#autostarting-on-boot)

### Create systemd service:
    sudo pico /etc/systemd/system/raspicam.service

### Add the config:
    [Unit]
    Description=raspivid
    After=network.target

    [Service]
    ExecStart=/bin/sh -c "/usr/bin/raspivid -n -w 640 -h 360 -b 1000000 -fps 15 -t 0 -o - | gst-launch-1.0 -v fdsrc ! h264parse ! rtph264pay config-interval=10 pt=96 ! udpsink host=192.168.192.101 port=5600"

    [Install]
    WantedBy=default.target

> The 192.168.192.101 is remote server IP
> [Raspberry Pi Camera settings document](https://www.raspberrypi.org/documentation/raspbian/applications/camera.md)

### Register the services:
    sudo systemctl daemon-reload
    sudo systemctl enable raspicam
    sudo systemctl start raspicam


### Testing: How to save video to disk?
Reference: https://gstreamer.freedesktop.org/data/doc/gstreamer/head/gstreamer-plugins/html/gstreamer-plugins-tee.html

The script below not work, if the stream didn't stop, the video will not be saved. 

    raspivid -n -w 1280 -h 720 -b 1000000 -fps 15 -t 0 -o - | gst-launch-1.0 -v fdsrc ! h264parse ! tee name=t t. ! queue ! rtph264pay config-interval=10 pt=96 ! udpsink host=192.168.192.102 port=5600 t. ! queue ! mp4mux ! filesink location=/home/bellergy/videos/testing.mp4

[Need to use C code to make it? Need to know how to pass remote button signal too.](https://github.com/crearo/gstreamer-cookbook/blob/master/README.md#startstop-recording-at-will)


### Testing: Multicast Streaming (Not work yet!!)

    raspivid -n -w 1280 -h 720 -b 1000000 -fps 15 -t 0 -o - | gst-launch-1.0 -v fdsrc ! h264parse ! rtph264pay config-interval=10 pt=96 ! udpsink host=

### Idea: Two 4G network to speed up/failsafe the conection?
https://www.thepolyglotdeveloper.com/2016/08/connect-multiple-wireless-networks-raspberry-pi/

---
## About Video Latency
[Video Encoding Basics](https://www.haivision.com/blog/all/video-encoding-basics-video-latency/)

---
## [References...](https://developer.ridgerun.com/wiki/index.php/Using_UDP_Multicast_with_GStreamer)

Mac video play scrtip:
```
gst-launch-1.0 -v udpsrc port=9000 caps='application/x-rtp, media=(string)video, clock-rate=(int)90000, encoding-name=(string)H264' ! rtph264depay ! avdec_h264 ! videoconvert ! autovideosink sync=f
```

[GStreamer Debugging](https://developer.ridgerun.com/wiki/index.php?title=GStreamer_Debugging)

[Video Bitrate Calculator](https://www.dr-lex.be/info-stuff/videocalc.html)

---

## Documents
[Offical docuemnt of Latency](https://gstreamer.freedesktop.org/documentation/tutorials/basic/index.html)
[Offical dpcument of Basic Tutorials for developer](https://gstreamer.freedesktop.org/documentation/tutorials/basic/index.html)
