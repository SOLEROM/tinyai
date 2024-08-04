# esp-tensorFlow helloWorld

```
make -f tensorflow/lite/micro/tools/make/Makefile TARGET=esp generate_hello_world_esp_project
cd tensorflow/lite/micro/tools/make/gen/esp_xtensa-esp32/prj/hello_world/esp-idf
idf.py menuconfig
idf.py build
```


```
Generated /tensor/esp/tensorflow/tensorflow/lite/micro/tools/make/gen/esp_xtensa-esp32/prj/hello_world/esp-idf/build/hello_world.bin

Project build complete. To flash, run this command:
/home/user/.espressif/python_env/idf4.4_py3.6_env/bin/python ../../../../../../../../../../../esp-idf/components/esptool_py/esptool/esptool.py -p (PORT) -b 460800 --before default_reset --after hard_reset --chip esp32  write_flash --flash_mode dio --flash_size detect --flash_freq 40m 0x1000 build/bootloader/bootloader.bin 0x8000 build/partition_table/partition-table.bin 0x10000 build/hello_world.bin
or run 'idf.py -p (PORT) flash'

```


Load and run the example

```
To flash (replace /dev/ttyUSB0 with the device serial port):

idf.py --port /dev/ttyUSB0 flash

Monitor the serial output:

idf.py --port /dev/ttyUSB0 monitor

Use Ctrl+] to exit.


```
