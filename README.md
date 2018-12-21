# Monarch-Controller
Control board for autonomous bio-mimetic butterfly drones. This board will convert the radio signal to servo commands, and feature some autopilot features by utilizing an IMU and Altimeter. We plan to have attitude/altitude hold, and by utilizing an infrared beacon and tracking system have off-system autonomous control.

# Features:
* SBUS input (PPM planned in the future, requires more annoying firmware)
* Telemetry output: serial or analog vbatt divider. (Possible smart-port compatibility down the road in firmware)
* Dual servo outputs
* Dual LED drivers: 1 PWM, 1 normal.
* Incredibly small/light profile: about 1in x 0.5in. Less than half the size of a standard FC!
* Integrated Altimeter and 9-dof IMU
* Open source, so write your own firmware!
* PWM LED can be repurposed as a third servo channel
* Low-power MSP430 microcontroller

# 3d Renders:
(Note: renders not up to date. Power/ground have been re-routed since then to avoid splitting the ground plane on the back.
<img src="https://i.imgur.com/szq5Si1.png" width="500">
<img src="https://i.imgur.com/quQAk56.png" width="500">
<img src="https://i.imgur.com/mdB33x4.png" width="500">

# Pics:
<img src="https://i.imgur.com/7ER366f.png?1" width="500">

# Known issues:
* Servo power/ground flipped relative to standard servo pins
* Should add resistors on serial lines and servo data pins for protection
* Remove soldermask on top layer for jtag pins

# Potential Changes/Upgrades
* Remove analog telemetry option
* Add third servo channel
* Integrated receiver (wifi)

# Fabrication
* Gerber files and BOM are in the "project outputs" folder. There are a few issues with rev A that are documented in the "known issues" section, although none are show-stoppers right now.
* We recommend PCBWay.com, and it was 5$ for 10 boards and 15$ for the stencil. Shipping can be pricey though, so make sure to buy a "non-framework" stencil.
* The BOM works out to abour 30-40$ per board depending on supplier and such. Much of that cost comes from plugs and the IMU and altimeter, which are optional depending on your use of this board.

# Use
* This board is intended to be used with either an SBUS receiver or a full duplex serial link, such as an xbee or esp8266. Using a full-duplex serial link should allow full telemetry and over-air reconfiguration for easy in-flight tuning of parameters such as PIDs and mixing algorithms.
* The two jumpers on the back allow the use of either serial telemetry or analog telemetry. Serial telemetry jumper must be shorted during configuration. IMPORTANT: only one jumper should be closed at at a time. We recommend using a 330-ohm resistor to short the serial port in order to provide some protection to shorts, although this will likely be integrated in later revisions.
* For configuration: Use a full-duplex serial link to your computer either using a usb-tty adapter or a wifi enabled board like the esp8266 and tcp/ip. A configuration utility is in developement in the Monarch-Connect repository.
* For SBUS: short the tx pin to ground in order to use SBUS input. The MCU will detect this and expect SBUS rather than standard serial. Note: this board only supports non-inverted SBUS. We recommend the usky receiver from fishpepper.de.
* For SBUS and analog telemetry: You may short the serial pin to ground *before* the jumper, while leaving the jumper open. Use a bodge-wire to do this. Then, you can close the analog jumper and use the analog telemetry. Future revisions will feature a 5-pin picoblade connector to prevent this annoying setup, or three seperate jumpers.
