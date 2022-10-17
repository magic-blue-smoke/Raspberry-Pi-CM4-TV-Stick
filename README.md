# Raspberry Pi CM4 TV Stick
Raspberry Pi CM4 that plugs directly to TV/monitor

## Specs
- Compatible with Raspberry Pi CM4 eMMC and no-eMMC
- HDMI plug
- Micro SD card connector
- USB-C connector for data/power
- Two USB2.0 USB-A connectors
- USB2.0 as solder pads on reverse side
- IR receiver
- User button
- USB multiplexer selector switch: enable 2xUSB-A ports or CM4 USB device mode
- Power and Act LEDs
- 14 GPIOs, as well as GND, 5V and 3.3V solder pads on reverse side of PCB for hacking 
- Connector for Ambilight-like lightning with WS2812 or WS2801 LEDs (GND, GPIO18, GPIO10 and GPIO11)

## Availability
Online store: https://mbs-shop.online/

Follow on Twitter: [@magic__smoke](https://twitter.com/magic__smoke)

![TV Stick](TVStickR4_4.jpeg)

![TV Stick](TVStickR4_5.jpeg)

## Description
### HDMI plug
The board has HDMI Type A plug and routed to CM4 HDMI0 port

### Micro SD card connector
Micro SD card connector accepts Micro SD card.

**Important**: don't insert SD card if using CM4 with eMMC, as SD card and/or CM4 can be permanently damaged (eMMC and SD card connector are sharing same SoC pins)

### USB-C connector
USB-C connector is used to provide power to TV Stick. Consider using Raspberry Pi 4 power adapter or known good power supply for Raspberry Pi 4

USB-C connector also has USB2.0 data lines multiplexed with USB-A connectors

### USB2.0 USB-A connectors
CM4 has built-in USB2.0 controller which can work as USB host or USB device. 
Slide switch, marked with A←USB→C on a back side of the boards configures CM4 USB controller and multiplexes USB data lines:
- When in `A` position: USB controller is switched to host mode and data lines are connected to USB2.0 switch IC and USB-A connectors are active
- When in `C` position: USB controller is switched to device mode and data lines are connected to USB-C connector. This mode can be used to flash CM4 eMMC or firmware

Latest Raspberry Pi OS builds have needed configuration line in `config.txt`

### IR receiver
IR receiver is connected to CM4 GPIO17. 
To enable IR receiver following line has to added to `config.txt` file: `dtoverlay=gpio-ir,gpio_pin=17`

[This article](https://devkimchi.com/2020/08/12/turning-raspberry-pi-into-remote-controller/) describes further remote pairing/learning (omit parts describing IR TX and make sure to still use 'dtoverlay=gpio-ir,**gpio_pin=17**') 

### User button 
User button is connected to GPIO14. When used, has to be configured as active low, input pull-up

Use scenarios:
- OS shutdown. To enable OS shutdown, add following line to `config.txt`: `dtoverlay=gpio-shutdown,gpio_pin=14`
- This button also tied to nRPIBOOT: hold on power on to enter USB MSD mode for eMMC programming/fw update. USB slide switch has to be in 'C' position

