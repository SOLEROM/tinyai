
## glibc diffs

* on host 2.31 compiled with 2.33 produce label_image using 2.33
* on fresh coral install 2.28

```

dev host:
    ldd --version ldd (Ubuntu GLIBC 2.31-0ubuntu9.14) 2.31


cross compiler:
   gcc-arm-10.3-2021.07-x86_64-aarch64-none-linux-gnu$ ./aarch64-none-linux-gnu/libc/usr/bin/ldd --version  ldd (GNU) 2.33

mendel fresh on target:
    ldd --version  ldd (Debian GLIBC 2.28-10) 2.28
    ldd label_image   version `GLIBC_2.33' not found
```

## build chroot with newer version (>2.33)

```

sudo debootstrap --arch=arm64 --foreign stable  coral_venv_stable http://ftp.debian.org/debian

sudo chroot /home/mendel/coral_venv_stable
/debootstrap/debootstrap --second-stage





in chroot stable:
        ldd --version   ldd (Debian GLIBC 2.36-9+deb12u3) 2.36


```


## pack and run

sudo tar cfz coral_venv_stable.tar coral_venv_stable
mdt push coral_venv_stable.tar

mtd shell
sudo tar xfz coral_venv_stable.tar 
sudo mount -o bind /sys  /home/mendel/coral_venv_stable/sys/
sudo mount -o bind /proc  /home/mendel/coral_venv_stable/proc
sudo mount -o bind /dev  /home/mendel/coral_venv_stable/dev
sudo cp /etc/resolv.conf coral_venv_stable/etc/resolv.conf

sudo chroot /home/mendel/coral_venv_stable

sudo mount -t devpts devpts /dev/pts

###  run1  build tflite for arm only

```
/label_image -m mobilenet_v1_1.0_224_quant.tflite -i   dog1.bmp  -l labels_mobilenet_quant_v1_224.txt -x 1
INFO: Loaded model mobilenet_v1_1.0_224_quant.tflite
INFO: resolved reporter
INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
INFO: XNNPACK delegate created.
INFO: Applied XNNPACK delegate.
INFO: invoked
INFO: average time: 37.221 ms
INFO: 0.772549: 204 West Highland white terrier
INFO: 0.0745098: 189 wire-haired fox terrier
INFO: 0.0392157: 200 Scotch terrier
INFO: 0.0313726: 191 Sealyham terrier
INFO: 0.027451: 193 cairn

```


