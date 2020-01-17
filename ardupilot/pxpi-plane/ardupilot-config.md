# ** For ArduPilot firmware ** 
## [1. Setup Elevon Planes](https://ardupilot.org/plane/docs/guide-elevon-plane.html)
- `SERVO1_FUNCTION` = 77 Elevon Left 
- `SERVO2_FUNCTION` = 78 Elevon Right
- `SERVO3_FUNCTION` = 70 Throttle

## [2. Servo Setup & Reversal](https://ardupilot.org/plane/docs/guide-elevon-plane.html#servo-setup-reversal)
 - Switch to `FBWA` flight mode and press the safety switch
 - Check the status:
    | Input      | Elevons Action       |
    | ---------- | -------------------- |
    | Roll right | Left 👆🏻 Right 👇🏻 |
    | Roll left  | Right 👆🏻 Left 👇🏻 |
    | Pitch down | Both 👆🏻            |
    | Pitch up   | Both 👇🏻            |

- Change `SERVO1_REVERSED` to correct left elevon direction
- Change `SERVO2_REVERSED` to correct right elevon direction

## [3. Verify RC Inputs](https://ardupilot.org/plane/docs/guide-elevon-plane.html#verify-rc-inputs)
 - Switch to `FBWA` flight mode and press the safety switch
 - Check the status:
    | RC Input         | Elevons Action       |
    | ---------------- | -------------------- |
    | Roll stick right | Left 👇🏻 Right 👆🏻 |
    | Roll stick left  | Right 👇🏻 Left 👆🏻 |
    | Pitch stick down | Both 👇🏻            |
    | Pitch stick up   | Both 👆🏻            |
- Switch to `MANUAL` flight mode and confirm the same behavior
- If need, change the [RC Input](https://ardupilot.org/plane/docs/rc-throw-trim.html#rc-throw-trim)

## [4. Servo Trim](https://ardupilot.org/plane/docs/guide-elevon-plane.html#servo-trim)
- Switch to `MANUAL` and leave the roll and pitch stick center
- Left and right elevons should be level
- If need, adjust `SERVO1_TRIM` and `SERVO2_TRIM` to level them

## [5. Servo Throw](https://ardupilot.org/plane/docs/guide-elevon-plane.html#servo-throw)
- Switch to `MANUAL` and move the roll and pitch stick
- If the servos have high pitched sound, the servo move too far
- Adjust `SERVO1_MIN`, `SERVO1_MAX`, `SERVO2_MIN`, `SERVO2_MAX` to correct them

## [6. ESC Calibration](https://ardupilot.org/plane/docs/guide-esc-calibration.html#typical-esc-calibration)
- start with the autopilot powered, but with the ESC unpowered and propeller removed
- switch to `MANUAL` flight mode
- disable the safety switch and arm the airplane
- move the throttle stick to maximum
- add power to the ESC

At this stage the ESC/motor should beep to indicate that it is in ESC calibration mode. Typically it will be 2 or 3 quick beeps, but the motor won’t turn.

- lower the throttle stick rapidly to zero
- the ESC should beep to indicate it has accepted the new calibration range
- slowly raise the throttle and check that the **motor responds correctly**

## 7. Calibration / Configation
- [x] [Radio Control](https://ardupilot.org/plane/docs/common-radio-control-calibration.html)
- [x] [ESC](https://ardupilot.org/plane/docs/guide-esc-calibration.html#typical-esc-calibration)
- [ ] [Accelerometer](https://ardupilot.org/plane/docs/common-accelerometer-calibration.html)
- [ ] [Compass](https://ardupilot.org/plane/docs/common-compass-calibration-in-mission-planner.html)
- [ ] [Battery](https://ardupilot.org/plane/docs/common-power-module-configuration-in-mission-planner.html)
- [ ] [Airspeed sensor](https://ardupilot.org/plane/docs/airspeed.html#software-configuration)\
  [Calibrating an Airspeed Sensor](https://ardupilot.org/plane/docs/calibrating-an-airspeed-sensor.html)

## [8. Flight Mode Setup](https://ardupilot.org/plane/docs/flight-modes.html)
For first flight:
1. CRUISE 
2. LOITER
3. AUTOTUNE \
--
4. FBWA
5. CIRCLE
6. RTL

> RC5_OPTION = 77 use channel 5 to swicth to TAKEOFF Mode

## [9. Setup Automatic Takeoff](https://ardupilot.org/plane/docs/automatic-takeoff.html#automatic-takeoff)
- `TKOFF_THR_MINACC` = 15 (When the acceleration trigger 15 m/s/s, auto takeoff start)
- `TKOFF_THR_DELAY` = 2 (0.2 sec. delay)
- `TKOFF_ALT` = 50

## [10. Failsafe](https://ardupilot.org/plane/docs/apms-failsafe-function.html)
- [ ] Check RC signal loss action
- [ ] Check GCS loss action
- 





# First Flght
## [1. Auto Tuning](https://ardupilot.org/plane/docs/automatic-tuning-with-autotune.html#automatic-tuning-with-autotune)


# After Flight
## [99. Center of Gravity](https://ardupilot.org/plane/docs/guide-center-of-gravity.html#guide-center-of-gravity)
- [Flying wing CG calculator](https://fwcg.3dzone.dk/)
- [Correct After First Flight](https://ardupilot.org/plane/docs/guide-center-of-gravity.html#correct-after-first-flight)




# ** For PX4 firmware ** 

## Select Airframe
Modified Parrot Disco

---
## Change Parameters
- BAT_V_EMPTY = 3.30v
- BAT_N_CELLS = 3S
- NAV_DLL_ACT = Retrun Mode
- NAV_GPSF_LT = 300s (how long it will loiter (circle) after losing GPS position)
- GF_MAX_VER_DIST = 400m
- RTL_RETURN_ALT = 300m
- MAV_1_CONFIG = TELEM 2
- SER_TEL2_BAUD = 115200
- 
