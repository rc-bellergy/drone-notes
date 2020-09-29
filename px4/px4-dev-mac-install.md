# Install PX4 Toolchain on Mac

## Reference:
https://dev.px4.io/master/en/setup/dev_env_mac.html

## Setup:

    pico ~/.zshenv

Edit the file:

    ulimit -S -n 2048
    # Point python to python 3 from Homebrew
    alias python=/usr/local/bin/python3
    # Point pip to python 3 pip
    alias pip=/usr/local/bin/pip3

Change to use zsh (if not using zsh):
- Open the Perefence of Terminal
- Change the Shell open with: Default login shell
- Open a new terminal

---

## Install:
    brew tap PX4/px4
    brew install px4-dev

### Issue:
    Error: px4-dev 1.6.5.0 is already installed
    To upgrade to 1.11.0, run `brew upgrade px4/px4/px4-dev`.

### Fixed:
    brew upgrade px4/px4/px4-dev

### Issue:
    Error: Cannot install osrf/simulation/gazebo11 because conflicting formulae are installed.
    gazebo9: because differing version of the same formula

### Fixed:
    brew unlink gazebo9
    brew upgrade px4/px4/px4-dev

## Install the required Python packages
    python3 -m pip install --user pyserial empy toml numpy pandas jinja2 pyyaml pyros-genmsg packaging

## Install SITL simulation with Gazebo
    brew cask install xquartz
    brew install px4-sim-gazebo

## Download the PX4 source code
    git clone https://github.com/PX4/Firmware.git --recursive

---

## Test build a jMAVSim simulator 
    cd Firmware
    make px4_sitl jmavsim

### Issue (only on my iMac):
The java version not match.

    Exception in thread "main" java.lang.UnsupportedClassVersionError: me/drton/jmavsim/Simulator has been compiled by a more recent version of the Java Runtime (class file version 58.0), this version of the Java Runtime only recognizes class file versions up to 57.0

### Not fix:
- Update the Java on Mac control panel
- Not work

---

## Build gazebo simulator

    make px4_sitl gazebo

### Issue

    #include <libavcodec/avcodec.h>
    1 error generated.
    ninja: build stopped: subcommand failed.
    FAILED: external/Stamp/sitl_gazebo/sitl_gazebo-build

Is `libavcodec` missing?


### Fix:

    brew upgrade ffmpeg

Then go to System Perferences > Software Update

---
## Build PX4 firmware for Pixracer
    make px4_fmu-v4_default

