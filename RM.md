# Rafalmag readme

## Changelog

### 2023-10-22

Latest stable Marlin release is 2.1.2.1

Thus checkout tag from `2.1.x` branch:

```bash
git checkout  2.1.2.1

``` 

And do a branch from it:

```bash
git switch -c 2.1.x-rm
```

For next release, just try to do:

```bash
git fetch --all
git rebase upstream/<new tag> ?
```


## Flashing via Octoprint (console)

Before flashing save output of `M503` Marlin command.

### On Windows

1. Platformio build, example successful output:
```
...
Compiling .pio\build\LPC1768\FrameworkArduino\main.cpp.o
Archiving .pio\build\LPC1768\libFrameworkArduino.a
Archiving .pio\build\LPC1768\lib82a\libU8glib-HAL.a
Archiving .pio\build\LPC1768\libCMSIS.a
Linking .pio\build\LPC1768\firmware.elf
Building .pio\build\LPC1768\firmware.bin
Checking size .pio\build\LPC1768\firmware.elf
Advanced Memory Usage is available via "PlatformIO Home > Project Inspect"
RAM:   [====      ]  44.0% (used 14404 bytes from 32736 bytes)
Flash: [====      ]  44.1% (used 209656 bytes from 475136 bytes)
=============== [SUCCESS] Took 71.95 seconds ===============

Environment    Status    Duration
-------------  --------  ------------
LPC1768        SUCCESS   00:01:11.950
=============== 1 succeeded in 00:01:11.950 ================
 *  Terminal will be reused by tasks, press any key to close it. 
```

2. Copy to OrangePi

```bash
scp .pio/build/LPC1768/firmware.bin rafal@192.168.50.164:~
OR
scp .pio/build/LPC1768/firmware.bin rafal@orangepipcplus:~
```

### On printer / via Octoprint UI
release media (M22)

### On OrangePi

SSH into OrangePI (from WSL):
```bash
ssh  rafal@orangepipcplus
```

On ssh:
```bash
sudo su
ls -l /dev/disk/by-id/
mount /dev/sda1 /media/usb/
cp /home/rafal/firmware.bin /media/usb/
ls -l /media/usb/
umount /media/usb/
```

### Restart printer

Then regarding EPPROM - from printers LCD / OctoPrint command interface:
- restore default settings - Reset all configurable settings to their factory defaults (M502)
- save - default settings in EEPROM - (M500)
- read the setting M503 and compare with `M503.txt` to reveal any differences
