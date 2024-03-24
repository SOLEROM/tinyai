# (2) mount rootfs from dw link

* deps
    sudo apt-get install -y simg2img
    sudo apt-get install qemu-user-static

* get u version
    on target:  cat /etc/mendel_version  (=> i got 5.3 )

* get the version from https://coral.ai/software/#mendel-linux

    wget https://dl.google.com/coral/mendel/enterprise/enterprise-eagle-20211117215217.zip

* convert img to raw:

    simg2img enterprise-eagle-20211117215217/rootfs_arm64.img ./rootfs_converted.raw.img

* mount that

    sudo mount -o loop  rootfs_converted.raw.img /mnt

* chroot that

    sudo chroot /mnt /bin/bash


* upgrade system
    
    apt-get upgrade



* build from helloWorld.c ; gcc and run inside container:

```

root@vladis:/# file /tmp/a.out 
/tmp/a.out: ELF 64-bit LSB pie executable, ARM aarch64, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux-aarch64.so.1, for GNU/Linux 3.7.0, BuildID[sha1]=08ca6cd2563feb328d57d9f68c7457aac28c8524, not stripped

root@vladis:/# ./tmp/a.out 
Hello, World!
root@vladis:/# 

```

## get newer cmake


## build ftlite

Build for AArch64 (ARM64)
This instruction shows how to build AArch64 binary which is compatible with Coral Mendel Linux 4.0, Raspberry Pi (with Ubuntu Server 20.04.01 LTS 64-bit installed).


git 

* in tflite build folder:

ARMCC_FLAGS="-funsafe-math-optimizations"
cmake -DCMAKE_C_FLAGS="${ARMCC_FLAGS}" \
  -DCMAKE_CXX_FLAGS="${ARMCC_FLAGS}" \
  -DCMAKE_VERBOSE_MAKEFILE:BOOL=ON \
  -DCMAKE_SYSTEM_NAME=Linux \
  -DCMAKE_SYSTEM_PROCESSOR=aarch64 \
  ../tensorflow/lite/


cmake --build . -j

cmake --build . -j -t benchmark_model

cmake --build . -j -t label_image