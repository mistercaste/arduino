# Arduino Samples

The guide below refers to an `AZ-Delivery Digispark Rev.3 USB Stick` on Linux (Debian/Ubuntu).

1. Install the [Arduino IDE](https://www.arduino.cc/en/software)
2. Go to folder ./.arduino15/packages/digistump/hardware/avr/1.6.7/libraries/DigisparkUSB, backup usbconfig.h to usbconfig.h.bak
3. In folder ./.arduino15/packages/digistump/hardware/avr/1.6.7/libraries/DigisparkUSB copy the provided usbconfig.h (this will mimic a Lenovo Laser Wireless Mouse)
4. Go to File &rarr; Preferences &rarr; Additional Boards Manager URLs &rarr; `http://digistump.com/package_digistump_index.json`
5. Tools &rarr; Board &rarr; Boards Manager &rarr; `Digistump AVR Boards`
6. `sudo adduser $USER dialout`
7. `sudo nano /etc/udev/rules.d/49-micronucleus.rules`
```
# UDEV Rules for Micronucleus boards including the Digispark.
# This file must be placed at:
#
# /etc/udev/rules.d/49-micronucleus.rules    (preferred location)
#   or
# /lib/udev/rules.d/49-micronucleus.rules    (req'd on some broken systems)
#
# After this file is copied, physically unplug and reconnect the board.
#
SUBSYSTEMS=="usb", ATTRS{idVendor}=="16d0", ATTRS{idProduct}=="0753", MODE:="0666"
KERNEL=="ttyACM*", ATTRS{idVendor}=="16d0", ATTRS{idProduct}=="0753", MODE:="0666", ENV{ID_MM_DEVICE_IGNORE}="1"
#
# If you share your linux system with other users, or just don't like the
# idea of write permission for everybody, you can replace MODE:="0666" with
# OWNER:="yourusername" to create the device owned by you, or with
# GROUP:="somegroupname" and mange access using standard unix groups.
```
6. `sudo udevadm control --reload-rules`
7. Tools &rarr; Board &rarr; Digistump AVR Boards &rarr; `Digispark (16mhz - No USB)`
8. Create a file (contents of this repo or samples)
9. Verify
10. Upload
11. Connect the USB stick
12. Done!

NOTE - The latest versions of Debian based kernels might neet to run `apt install libusb-0.1-4`
