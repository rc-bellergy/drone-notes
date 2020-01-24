# Video Streaming
[Raspberry Pi Camera settings document](https://www.raspberrypi.org/documentation/raspbian/applications/camera.md)

## [Video Streaming](https://docs.emlid.com/navio/common/dev/video-streaming/)
Raspbarry Pi video streaming start up script:
- [raspivid](https://www.raspberrypi.org/documentation/raspbian/applications/camera.md) is the command line tool for capturing video with the camera module of Raspbarry Pi
- [gst-launch-1.0](https://gstreamer.freedesktop.org/documentation/tools/gst-launch.html) build and run a GStreamer pipeline
- [Gstreamer basic real time streaming tutorial](http://www.einarsundgren.se/gstreamer-basic-real-time-streaming-tutorial/)

### Install gstreamer1.0
    sudo apt-get update
    sudo apt-get install gstreamer1.0-tools gstreamer1.0-plugins-good gstreamer1.0-plugins-bad

### Start vieo streaming script
    raspivid -n -w 1280 -h 720 -b 1000000 -fps 15 --flush --timeout 0 -o - | gst-launch-1.0 -v fdsrc ! h264parse ! rtph264pay config-interval=10 pt=96 ! udpsink host=192.168.192.101 port=5600

> The 192.168.192.101 is remote server IP


#### Remarks of raspivid options
| Options        | Descriptions                                                                                                                                                                                                                   |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| --nopreview    | No preview window                                                                                                                                                                                                              |
| --bitrate      | bitrate (1000000 = 10Mbits/s)                                                                                                                                                                                                  |
| --timeout 0    | timeout 0 = run continuously                                                                                                                                                                                                   |
| -o -           | output file '-' all output is sent to stdout                                                                                                                                                                                   |
| --vstab        | Turn on video stabilisation                                                                                                                                                                                                    |
| -ex auto/night | Exposure auto or night mode                                                                                                                                                                                                    |
| --flush        | (Tested, don't use it in the slow network. It will make 'gray screen' randomly) Forces a flush of output data buffers as soon as video data is written. This bypasses any OS caching of written data, and can decrease latency |

Adjust bitrate with -b switch or -fps if your video lags behind.

---
#### Remarks of gstreamer pipeline
| Options    | Descriptions                                                      |
| ---------- | ----------------------------------------------------------------- |
| -v         | Output status information                                         |
| fdsrc      | source from unix file descriptor (raspivid's output in this case) |
| h264parse  | convert the source to h264 format                                 |
| rtph264pay | Payload-encode H264 video into RTP packets (ready for streaming)  |
| udpsink    | stream the video to the UDP address                               |

## Save video to disk
The script will save a .h264 video file and stream the video to an IP:PORT at same time.

```sh
NOW=$(date +"%Y-%m-%d")
VIDEO_FILE=${PWD}/videos/$NOW-livecam.h264
UDP_IP=192.168.192.104 # The receiver IP
UDP_PORT=5600

/usr/bin/raspivid -n -w 1280 -h 720 -rot 180 -b 1500000 -fps 25 -vs -drc high -t 0 -o - | \
tee $VIDEO_FILE | \
/usr/bin/gst-launch-1.0 -v fdsrc ! \
h264parse ! rtph264pay config-interval=10 pt=96 ! \
udpsink host=$UDP_IP port=$UDP_PORT
```

### Convert the .h264 video to .mp4 format
Install the MP4BOX \
`sudo apt install -y gpac`

Convert \
`MP4Box -add input.h264 output.mp4`

---
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
[Offical docuemnt of gstreamer](https://gstreamer.freedesktop.org/documentation/tutorials/basic/index.html)
