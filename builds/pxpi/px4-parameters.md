# Parameters 

## Joystac
COM_RC_IN_MODE  RC Transmitter / Joystick (when use datalink)

## Failsafe
NAV_RCL_ACT     Return Mode

## Position
MPC_XY_CRUISE   12 m/s (RTL/Auto modes speed) 
MPC_XY_MANUAL   15 m/s (Manuel control speed)
MPC_XY_VEL_MAX  18 m/s
MPC_MANTHR_MIN  8%

## Takeoff
MIS_TAKEOFF_ALT 10 m    (Take-off altitude)
MPC_TKO_SPEED   1.5 m   (Takeoff climb rate)

## Landing
LNDMC_XY_VEL_MAX    1.5 m/s (Max speed when landing)
LNDMC_Z_VEL_MAX     0.5 m   (Max climb rate [up/down])

## ESC
DSHOT_CONFIG    Disable (use PWM)
PWM_MIN         935

## ESC (Not in use because motor sync issue)
DSHOT_CINFIG    DShot150
DSHOT_MIN       0.04%
MOT_POLE_COUNT  28 (T-Motor MN5006)

## ARM
COM_DISARM_LAND     1 s
MPC_SPOOLUP_TIME    2 s

## Others
MC_AIRMODE      Disable (it will make the motor spin very fast when arm, don't know reason)


