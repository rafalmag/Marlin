## Flashing via Octoprint

# Windows
Platformio build
```
scp .pio/build/LPC1768/firmware.bin rafal@192.168.1.10:~
```

# On printer
release media

# On OrangePi
```
ssh  rafal@192.168.1.10
sudo su
ls -l /dev/disk/by-id/
mount /dev/sda1 /media/usb/
cp /home/rafal/firmware.bin /media/usb/
ls -l /media/usb/
umount /media/usb/
```

# Restart printer

Then regarding EPPROM - from printers LCD:
- restore failsafe - Reset all configurable settings to their factory defaults (M502)
- save - To also reset settings in EEPROM - (M500)

(Reset settings and save them to EEPROM: M502;M500;)
