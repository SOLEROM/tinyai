# helloWorld

##

```

idf.py set-target esp32

idf.py menuconfig


idf.py build


```

```
Project build complete. To flash, run this command:
/home/user/.espressif/python_env/idf4.4_py3.6_env/bin/python ../../esp-idf/components/esptool_py/esptool/esptool.py -p (PORT) -b 460800 --before default_reset --after hard_reset --chip esp32  write_flash --flash_mode dio --flash_size detect --flash_freq 40m 0x1000 build/bootloader/bootloader.bin 0x8000 build/partition_table/partition-table.bin 0x10000 build/hello-world.bin
or run 'idf.py -p (PORT) flash'

```

## flash

* Flash the binaries that you just built (bootloader.bin, partition-table.bin and hello-world.bin) onto your ESP32 board by running:

```
idf.py -p /dev/ttyUsbXXXX [-b BAUD] flash
```
