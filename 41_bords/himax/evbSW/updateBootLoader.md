# updateBootLoader

## prepare

* linuxDriver

```
wget https://www.ftdichip.com/Support/SoftwareExamples/libft4222-linux-1.4.4.9.tgz

./install4222.sh

/etc/udev/rules.d/99-ftdi.rules
===============================
# FTDI's ft4222 USB-I2C Adapter
SUBSYSTEM=="usb", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="601c", GROUP="plugdev", MODE="0666"

```

* Flash tool

```
wget https://github.com/HimaxWiseEyePlus/bsp_tflu/releases/download/v1.0/FlashTool.zip

```

* bootloader blob

```
wget https://github.com/HimaxWiseEyePlus/bsp_tflu/releases/download/v1.0/himax_we1_bootloader_v1_4_4.bin
```

## update

```
Copy bootloader to FlashTool directory.

Connect HIMAX WE1 EVB via USB cable.

Make sure there is no serial terminal connect to HIMAX WE1 EVB

Type following command to start update flash image

./WE-I_ISP_Tool [bootloader name]

```
