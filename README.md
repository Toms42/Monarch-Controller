# Monarch-Controller
Control board for autonomous bio-mimetic butterfly drones. This board will convert the radio signal to servo commands, and feature some autopilot features by utilizing an IMU and Altimeter. We plan to have attitude/altitude hold, and by utilizing an infrared beacon and tracking system have off-system autonomous control.

# Features:
* SBUS input (PPM planned in the future, requires more annoying firmware)
* Telemetry output: smart-port or analog vbatt divider
* Dual servo outputs
* Dual LED drivers: 1 PWM, 1 normal.
* Incredibly small/light profile: about 1in x 0.5in. Less than half the size of a standard FC!
* Integrated Altimeter and IMU
* Open source, so write your own firmware!
* PWM LED can be repurposed as a third servo channel
* Low-power MSP430 microcontroller

# 3d Renders:
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
