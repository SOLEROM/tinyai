# Download APP

* connect HIMAX WE1 EVB with micro usb cable, check device ID by typing

```
ls /sys/bus/usb-serial/devices/ -ltrah
```

* minicom

```
minicom -wD /dev/tty ???

```

* Reset WE1 EVB by press reset button, then press any keyboard key (except enter key) in 0.3 sec.
* Press button 1 and WE1 EVB will enter receiving mode 
* Ctrl+A to enter minicom menu then Press s button to upload file and select "xmodem".
* Fill target flash image path and image name ("_0.img" and then "_1.img" if multiple images)

