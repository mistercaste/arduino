# Arduino Samples
A collection of code for fun.

The guide below refers to a quickstart for a AZ-Delivery Digispark Rev.3 USB Stick.

1. Install the [Arduino IDE](https://www.arduino.cc/en/software)
2. Go to File --> Preferences --> Additional Boards Manager URLs --> http://digistump.com/package_digistump_index.json
3. Tools --> Board --> Boards Manager --> Digistump AVR Boards
4. sudo adduser $USER dialout
5. sudo nano /etc/udev/rules.d/49-micronucleus.rules
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
6. sudo udevadm control --reload-rules
7. Tools --> Board --> Digistump AVR Boards --> Digispark (16mhz - No USB)
8. Create a file (contents of this repo or samples)
9. Verify
10. Upload
11. Connect USB
12. Done!
