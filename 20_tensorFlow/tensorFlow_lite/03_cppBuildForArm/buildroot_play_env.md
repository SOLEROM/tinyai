
# buildroot 

* inside tfdocker

```
apt-get install libncurses-dev kpartx file build-essential ncurses-base ncurses-bin libncurses5-dev dialog bc cpio
apt-get install qemu-system-arm vim

mkdir /buildroot
cd /buildroot/
git clone git://git.buildroot.net/buildroot
```

```

make qemu_arm_vexpress_defconfig 

make menuconfig
```


* to build with the same toolchain of tflight

```
     Toolchain type (External toolchain)  --->                                                                │ │  
  │ │                                           *** Toolchain External Options ***                                                                       │ │  
  │ │                                           Toolchain (Custom toolchain)  --->                                                                       │ │  
  │ │                                           Toolchain origin (Pre-installed toolchain)  --->                                                         │ │  
  │ │                                       (/root/toolchains/arm-gnu-toolchain-11.3.rel1-x86_64-arm-none-linux-gnueabihf) Toolchain path                │ │  
  │ │                                       (arm-none-linux-gnueabihf) Toolchain prefix                                                                  │ │  
  │ │                                           External toolchain gcc version (11.x)  --->                                                              │ │  
  │ │                                           External toolchain kernel headers series (4.20.x)  --->                                                  │ │  
  │ │                                           External toolchain C library (glibc)  --->                                                               │ │  
  │ │                                       [*] Toolchain has SSP support?                                                                               │ │  
  │ │                                       [*]   Toolchain has SSP strong support?                                                                      │ │  
  │ │                                       [ ] Toolchain has RPC support?                                                                               │ │  
  │ │                                       [*] Toolchain has C++ support?
```

## overlay
* copy to buildroot overlay folder all the data need to the roofs
* for example

```
wget https://storage.googleapis.com/download.tensorflow.org/models/mobilenet_v1_2018_02_22/mobilenet_v1_1.0_224.tgz
targz to overlay the needed files
cp /tensorflow_src/tensorflow/lite/examples/label_image/testdata/grace_hopper.bmp
cp <tensor-flow-cmake-build>/label_image arm elf to overlay

```
## build

```
make BR2_TARGET_ROOTFS_EXT2_SIZE="500M" BR2_JLEVEL=4 BR2_ROOTFS_OVERLAY=./overlay/
```

```
ls output/images/
rootfs.ext2  start-qemu.sh  versatile-pb.dtb  zImage
```

## emulator run 

```
qemu-system-arm -M vexpress-a9 -kernel output/images/zImage -dtb output/images/vexpress-v2p-ca9.dtb -drive file=output/images/rootfs.ext2,if=sd,format=raw -append "console=ttyAMA0,115200 rootwait root=/dev/mmcblk0"  -net nic,model=lan9118 -nographic

```

* pass: root
* files from overlay are in /

