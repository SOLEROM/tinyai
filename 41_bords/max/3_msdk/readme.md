# MSDK

 * used to compile, flash, and debug the output of the ai8x-synthesis (“izer”) tool
 * enables general software development for the microcontroller cores

* containe:
```
Peripheral Drivers
Board Support Packages (BSPs)
Libraries
Examples
Toolchain
    Arm GCC
    RISC-V GCC
    Make
    OpenOCD
```



## Toolchain Setup


install the MSDK via the Automatic Installer.

```
sudo apt update && sudo apt install libxcb-glx0 libxcb-icccm4 libxcb-image0 libxcb-shm0 libxcb-util1 libxcb-keysyms1 libxcb-randr0 libxcb-render-util0 libxcb-render0 libxcb-shape0 libxcb-sync1 libxcb-xfixes0 libxcb-xinerama0 libxcb-xkb1 libxcb1 libxkbcommon-x11-0 libxkbcommon0 libgl1 libusb-0.1-4 libhidapi-libusb0 libhidapi-hidraw0

<cd to git folder of msdk git clone>
cd Tools
mkdir SDK_install_root

sudo ./MaximMicrosSDK_linux.run in --root /data/tinyai/maxCNN/sdk/Tools/SDK_install_root

ln -s /data/tinyai/maxCNN/sdk/Tools/SDK_install_root/Tools/GNUTools GNUTools
ln -s /data/tinyai/maxCNN/sdk/Tools/SDK_install_root/Tools/OpenOCD  OpenOCD
ln -s /data/tinyai/maxCNN/sdk/Tools/SDK_install_root/Tools/xPack    xPack
```


```
brew install libusb-compat libftdi hidapi libusb
```


```
# MSDK location
MAXIM_PATH=/data/tinyai/maxCNN/sdk/  # Change me!
export MAXIM_PATH

# Arm GCC -- adjust version number
ARMGCC_DIR=$MAXIM_PATH/Tools/GNUTools/10.3
echo $PATH | grep -q -s "$ARMGCC_DIR/bin"
if [ $? -eq 1 ] ; then
    PATH=$PATH:"$ARMGCC_DIR/bin"
    export PATH
    export ARMGCC_DIR
fi

# RISC-V GCC -- adjust version number
RISCVGCC_DIR=$MAXIM_PATH/Tools/xPack/riscv-none-embed-gcc/10.2.0-1.2
echo $PATH | grep -q -s "$RISCVGCC_DIR/bin"
if [ $? -eq 1 ] ; then
    PATH=$PATH:"$RISCVGCC_DIR/bin"
    export PATH
    export RISCVGCC_DIR
fi

# OpenOCD
OPENOCD_DIR=$MAXIM_PATH/Tools/OpenOCD
echo $PATH | grep -q -s "$OPENOCD_DIR"
if [ $? -eq 1 ] ; then
    PATH=$PATH:$OPENOCD_DIR
    export PATH
    export OPENOCD_DIR
fi

```


## check

```
arm-none-eabi-gdb -v
make -v
openocd -v
```
