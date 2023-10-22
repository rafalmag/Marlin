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


## Flashing via Octoprint

### Windows
Platformio build (2021)
```bash
scp .pio/build/LPC1768/firmware.bin rafal@192.168.1.10:~
OR
scp .pio/build/LPC1768/firmware.bin rafal@orangepipcplus:~
```

### On printer (2021)
release media (M22)

### On OrangePi (2021)
```bash
ssh  rafal@192.168.1.10
sudo su
ls -l /dev/disk/by-id/
mount /dev/sda1 /media/usb/
cp /home/rafal/firmware.bin /media/usb/
ls -l /media/usb/
umount /media/usb/
```

### Restart printer (2021)

Then regarding EPPROM - from printers LCD:
- restore failsafe - Reset all configurable settings to their factory defaults (M502)
- save - To also reset settings in EEPROM - (M500)

(Reset settings and save them to EEPROM: M502;M500;)
