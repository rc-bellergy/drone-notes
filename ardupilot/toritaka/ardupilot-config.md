# ** For ArduPilot firmware ** 
## [1. Setup Elevon Planes](https://ardupilot.org/plane/docs/guide-elevon-plane.html)
- `SERVO1_FUNCTION` = 77 Elevon Left 
- `SERVO2_FUNCTION` = 78 Elevon Right
- `SERVO3_FUNCTION` = 70 Throttle
- `SERVO1_REVERSED` = Reversed
- `RC1_REVERSED` = Reversed

## [2. Servo Setup & Reversal](https://ardupilot.org/plane/docs/guide-elevon-plane.html#servo-setup-reversal)
 - Switch to `FBWA` flight mode and press the safety switch
 - Check the status:
    | Input      | Elevons Action       | Action     |
    | ---------- | -------------------- | ---------- |
    | Roll right | Left 👆🏻 Right 👇🏻 | Roll left  |
    | Roll left  | Left 👇🏻 Right 👆🏻 | Roll right |
    | Pitch down | Both 👆🏻            | Pull up    |
    | Pitch up   | Both 👇🏻            | Pull down  |

- Change `SERVO1_REVERSED` to correct left elevon direction
- Change `SERVO2_REVERSED` to correct right elevon direction

## [3. Verify RC Inputs](https://ardupilot.org/plane/docs/guide-elevon-plane.html#verify-rc-inputs)
 - Switch to `FBWA` flight mode and press the safety switch
 - Check the status:
    | RC Input         | Elevons Action       | ACtion     |
    | ---------------- | -------------------- | ---------- |
    | Roll stick right | Left 👇🏻 Right 👆🏻 | Roll right |
    | Roll stick left  | Left 👆🏻 Right 👇🏻 | Roll left  |
    | Pitch stick down | Both 👆🏻            | Pull up    |
    | Pitch stick up   | Both 👇🏻            | Pull down  |
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
- [x] [Accelerometer](https://ardupilot.org/plane/docs/common-accelerometer-calibration.html)
- [x] [Compass](https://ardupilot.org/plane/docs/common-compass-calibration-in-mission-planner.html)
- [x] [Battery](https://ardupilot.org/plane/docs/common-power-module-configuration-in-mission-planner.html)
- [ ] [Airspeed sensor](https://ardupilot.org/plane/docs/airspeed.html#software-configuration)\
  [Calibrating an Airspeed Sensor](https://ardupilot.org/plane/docs/calibrating-an-airspeed-sensor.html)

## [8. Flight Mode Setup](https://ardupilot.org/plane/docs/flight-modes.html)
For first flight:
1. CRUISE 
3. TAKEOFF (#13)
2. FBWA \
--
4. LOITER
5. AUTOTUNE
6. FBWA

## [9. Setup Automatic Takeoff](https://ardupilot.org/plane/docs/automatic-takeoff.html#automatic-takeoff)
- `TKOFF_THR_MINACC` = 15 (When the acceleration trigger 15 m/s/s, auto takeoff start)
- `TKOFF_THR_DELAY` = 2 (0.2 sec. delay)
- `TKOFF_ALT` = 50
- `TKOFF_THR_MINSPD` = 4 m/s

## [10. Failsafe](https://ardupilot.org/plane/docs/apms-failsafe-function.html)
- [x] Check RC signal loss action
- [ ] Check GCS loss action

## 11. Additional parameters settings:
