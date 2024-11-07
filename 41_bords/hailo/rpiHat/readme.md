# hailo for rpi

* https://www.geektime.co.il/raspberry-pi-will-use-israeli-ai-chips/
* https://www.raspberrypi.com/documentation/accessories/ai-kit.html

getting started:

https://www.raspberrypi.com/documentation/computers/ai.html



## qemu rpi


sudo apt install qemu qemu-system qemu-user-static


```

> xz -d  2024-10-22-raspios-bookworm-arm64-full.img.xz

> file 2024-10-22-raspios-bookworm-arm64-full.img
2024-10-22-raspios-bookworm-arm64-full.img: DOS/MBR boot sector; partition 1 : ID=0xc, start-CHS (0x40,0,1), end-CHS (0x3ff,3,32), startsector 8192, 1048576 sectors; partition 2 : ID=0x83, start-CHS (0x3ff,3,32), end-CHS (0x3ff,3,32), startsector 1056768, 28786688 sectors


> fdisk -l 2024-10-22-raspios-bookworm-arm64-full.img
Disk 2024-10-22-raspios-bookworm-arm64-full.img: 14.23 GiB, 15279849472 bytes, 29843456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x60691ba7

Device                                      Boot   Start      End  Sectors  Size Id Type
2024-10-22-raspios-bookworm-arm64-full.img1         8192  1056767  1048576  512M  c W95 FAT32 (LBA)
2024-10-22-raspios-bookworm-arm64-full.img2      1056768 29843455 28786688 13.7G 83 Linux


8192

```

```
 sudo mount -o loop,offset=$((512 * 8192)) 2024-10-22-raspios-bookworm-arm64-full.img /mnt/

/mnt

bcm2710-rpi-2-b.dtb       bcm2711-rpi-400.dtb     bcm2712-rpi-5-b.dtb         cmdline.txt   fixup_cd.dat    issue.txt         start4db.elf  start_x.elf
bcm2710-rpi-3-b.dtb       bcm2711-rpi-4-b.dtb     bcm2712-rpi-cm5-cm4io.dtb   config.txt    fixup.dat       kernel_2712.img   start4.elf
bcm2710-rpi-3-b-plus.dtb  bcm2711-rpi-cm4.dtb     bcm2712-rpi-cm5-cm5io.dtb   fixup4cd.dat  fixup_db.dat    kernel8.img       start4x.elf
bcm2710-rpi-cm3.dtb       bcm2711-rpi-cm4-io.dtb  bcm2712-rpi-cm5l-cm4io.dtb  fixup4.dat    fixup_x.dat     LICENCE.broadcom  start_cd.elf
bcm2710-rpi-zero-2.dtb    bcm2711-rpi-cm4s.dtb    bcm2712-rpi-cm5l-cm5io.dtb  fixup4db.dat  initramfs_2712  overlays          start_db.elf
bcm2710-rpi-zero-2-w.dtb  bcm2712d0-rpi-5-b.dtb   bootcode.bin                fixup4x.dat   initramfs8      start4cd.elf      start.elf

```

