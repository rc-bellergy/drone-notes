# Pixhawk Setup
## Reference from: https://www.youtube.com/watch?v=WVI7B4IfdKI 

```
Download RadioLink MP
Plug in USB, PX4 FLOW shows in device manager
In MP go to Initial Setup -> Install firmware, select plane, follow instructions
Connect
  If via radio, 57600 baud. 'Access denied' might be fixed by unplugging radio.
Initial setup -> Mandatory hardware
  Calibrate accel
  Calibrate radio (reverse pitch channel)
  Set flight modes: manual, FBWA, AUTOTUNE (set FLTMODE_CH if you don't want ch8) Check.
Mount everything in plane
  Left servo ch1, right servo ch2, ESC ch3
  Set SERVO1_FUNCTION left elevon, SERVO2_FUNCTION right elevon (77,78)
  Set SERVO2_REVERSED to 1
  Set SERVO1_TRIM, SERVO2_TRIM if necessary.
  Set SERVO1_MIN, SERVO1_MAX etc if necessary.
Set plane level and do 'Calibrate level' part of Accel calibration page.
Calibrate compasses
Calibrate ESC
In Battery Monitor set 'Voltage and Current', 'Other', 'The Cube or Pixhawk'. Enter value in 'Voltage divider (calced)'.
If no SD card inserted, set ARMING_CHECK to remove 'Logging available' check (1024).

Set trims to neutral in radio and adjust linkages to suit.
Check directions of elevons. Check compass direction is correct.

ALT_HOLD_RTL 8000 cm
WP_LOITER_RAD 100 m

Optional hardware -> Camera gimbal
  Shutter: SERVO5
  Pushed: 1900
  Duration: 7
  (only works when hardware arm enabled)
```
## Other Reference: https://www.youtube.com/watch?v=ltVIKNZhIQQ

## [FAQ](http://ardupilot.org/plane/docs/fixed-wing-faq.html)