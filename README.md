# Banc Sonore
## for Monac1: http://www.monac1.fr

Rpi3 (read-only file system) based autonomous wav player.

When GPIO7 is grounded, a wavfile is randomly chosen from USB disk's root directory and played.  
Files must be 44100Hz/16bit format.

- Fade up time: 20ms (declick)
- Fade down: after 1s switch off, 2s fade down then stop. If switch back on, 500ms fade up.

### USB disk automounting hack

Because the filesystem is read-only, it cannot create a folder in /media when a USB disk is connected.
So a **/media/usbhd** folder is created at config time and given to user **pi**, while the filesystem is mounted RW, and a special rule is added to **udev**: 

```
- sudo mkdir /media/usbhd
- sudo chown pi:pi /media/usbhd
- sudo cp 11-auto-mount-usb-to-usbhd.rules /etc/udev/rules.d
```

### GPIO switch pinout:

                    1   2
                    3   4
                    5   6
       ---> GPIO-7  7   8
       ---> GND     9   10
                    11  12
                    13  14
                    15  16
                    17  18
                    19  20 
                    21  22
                    23  24
                    25  26
                    27  28
                    29  30
                    31  32
                    33  34
                    35  36
                    37  38
                    39  40
                    