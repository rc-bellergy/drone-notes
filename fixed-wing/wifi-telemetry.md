# Connect WiFi module to Pixhawk

## Document
[ESP8266 wifi telemetry](http://ardupilot.org/copter/docs/common-esp8266-telemetry.html?highlight=wifi)

## WiFi Module
[ATK-ESP8266](https://detail.tmall.com/item.htm?id=581982859981&spm=a1z09.2.0.0.639f2e8dBz9VVv&_u=t1l42deacc19)

## Flashing ArduPilot firmware to ATK-ESP8266
1. Download ESP FLASH DOWNLOAD TOOL V0.9.6
2. Download firmware [firmware-esp01_1m.bin](http://firmware.ardupilot.org/Tools/MAVESP8266/latest/firmware-esp01_1m.bin)
3. Setup: SPI MODE: DOUT, OFFSET: 0x00000, FLASH SIZE: 8Mbit, BAYDRATE: 115200, (others default)

## My WiFi Setup
    SSID: BellergyPixhawk
    Password: dodo6162
    Admin Page: http://192.168.4.1