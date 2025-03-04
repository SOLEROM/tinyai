


rock-5b_bookworm_kde_b5.output.img: DOS/MBR boot sector; partition 1 : ID=0xee, start-CHS (0x0,0,2), end-CHS (0x391,201,50), startsector 1, 14680057 sectors, extended partition table (last)

Device                               Start      End  Sectors  Size Type
rock-5b_bookworm_kde_b5.output.img1  32768    65535    32768   16M Linux filesystem
rock-5b_bookworm_kde_b5.output.img2  65536   679935   614400  300M Linux filesystem
rock-5b_bookworm_kde_b5.output.img3 679936 14680024 14000089  6.7G Linux filesystem


sudo mount -o loop,offset=$((512 * 32768)) rock-5b_bookworm_kde_b5.output.img ./mnt1/
sudo mount -o loop,offset=$((512 * 65536)) rock-5b_bookworm_kde_b5.output.img ./mnt2/
sudo mount -o loop,offset=$((512 * 679936)) rock-5b_bookworm_kde_b5.output.img ./mnt3/


mnt1/
├── before.txt
└── config.txt


0% ./mnt2


./mnt3/
bin  boot  config  dev  etc  home  lib  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var


sudo cp /usr/bin/qemu-aarch64-static ./mnt3/usr/bin/
sudo cp /etc/resolv.conf ./mnt3/etc/


# chroot
sudo mount -o bind /dev ./mnt3/dev
sudo mount -o bind /sys ./mnt3/sys
sudo mount -o bind /proc ./mnt3/proc
sudo mount -o bind /dev/pts ./mnt3/dev/pts
sudo chroot ./mnt3 /bin/bash


