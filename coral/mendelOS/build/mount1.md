

file ./out/target/product/mt8167s_excelsior/obj/ROOTFS/rootfs_arm64.raw.img
./out/target/product/mt8167s_excelsior/obj/ROOTFS/rootfs_arm64.raw.img: Linux rev 1.0 ext4 filesystem data, UUID=7621b0ec-e086-4d89-a0e6-b92cda7353d5 (needs journal recovery) (extents) (64bit) (large files) (huge files)


sudo mount -o loop ./out/target/product/mt8167s_excelsior/obj/ROOTFS/rootfs_arm64.raw.img /mnt/
sudo DEBIAN_FRONTEND=noninteractive DEBCONF_NONINTERACTIVE_SEEN=true LC_ALL=C LANGUAGE=C LANG=C chroot /mnt /bin/bash