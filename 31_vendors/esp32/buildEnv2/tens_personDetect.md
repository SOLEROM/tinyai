#

* person_detection example requires an external component esp32-camera for functioning hence we will have to manually clone it in components/ directory

* prepare

```
make -f tensorflow/lite/micro/tools/make/Makefile TARGET=esp generate_person_detection_esp_project
cd tensorflow/lite/micro/tools/make/gen/esp_xtensa-esp32/prj/person_detection/esp-idf/
git clone https://github.com/espressif/esp32-camera.git components/esp32-camera

```

* config cam

```

> idf.py menuconfig

(Top) → Camera Pins → Select Camera Pinout
                                                Espressif IoT Development Framework Configuration
( ) WROVER-KIT With OV2640 Module
( ) ESP_EYE DevKit
( ) M5Stack Camera With PSRAM
( ) M5Stack Camera F (Wide)
(X) ESP32-CAM by AI-Thinker
( ) Custom Camera Pinout
```

* bugs?

```
vi +19 main/person_model_grayscale/person_detect_model_data.cc 
//qteam//#include "../../person_detection/person_detect_model_data.h"
#include "../../main/person_detect_model_data.h"


```

* build

```
> idf.py build
Executing action: all (aliases: build)
Project build complete. To flash, run this command:
/home/user/.espressif/python_env/idf4.4_py3.6_env/bin/python ../../../../../../../../../../../esp-idf/components/esptool_py/esptool/esptool.py -p (PORT) -b 460800 --before default_reset --after hard_reset --chip esp32  write_flash --flash_mode dio --flash_size detect --flash_freq 80m 0x1000 build/bootloader/bootloader.bin 0x8000 build/partition_table/partition-table.bin 0x10000 build/person_detection.bin
or run 'idf.py -p (PORT) flash'
 


```


* flash

```
[CONT]user@vostro14:/tensor/esp/tensorflow/tensorflow/lite/micro/tools/make/gen/esp_xtensa-esp32/prj/person_detection/esp-idf$ idf.py -p /dev/ttyUSB1 flash
Executing action: flash
Running ninja in directory /tensor/esp/tensorflow/tensorflow/lite/micro/tools/make/gen/esp_xtensa-esp32/prj/person_detection/esp-idf/build
Executing "ninja flash"...
[1/4] Performing build step for 'bootloader'
ninja: no work to do.
[1/2] cd /tensor/esp/esp-idf/components/esptool_py && /usr/bin/cmake -D...ild" -P /tensor/esp/esp-idf/components/esptool_py/run_serial_tool.cmake
esptool.py esp32 -p /dev/ttyUSB1 -b 460800 --before=default_reset --after=hard_reset write_flash --flash_mode dio --flash_freq 80m --flash_size 4MB 0x8000 partition_table/partition-table.bin 0x1000 bootloader/bootloader.bin 0x10000 person_detection.bin
esptool.py v3.1-dev
Serial port /dev/ttyUSB1
Connecting....
Chip is ESP32-D0WD (revision 1)
Features: WiFi, BT, Dual Core, 240MHz, VRef calibration in efuse, Coding Scheme None
Crystal is 40MHz
MAC: c8:2b:96:a1:6c:34
Uploading stub...
Running stub...
Stub running...
Changing baud rate to 460800
Changed.
Configuring flash size...
Compressed 3072 bytes to 103...
Writing at 0x00008000... (100 %)
Wrote 3072 bytes (103 compressed) at 0x00008000 in 0.1 seconds (effective 412.9 kbit/s)...
Hash of data verified.
Compressed 26768 bytes to 16505...
Writing at 0x00001000... (50 %)
Writing at 0x000077f9... (100 %)
Wrote 26768 bytes (16505 compressed) at 0x00001000 in 0.8 seconds (effective 269.6 kbit/s)...
Hash of data verified.
Compressed 734592 bytes to 444704...
Writing at 0x00010000... (3 %)
Writing at 0x00017364... (7 %)
Writing at 0x0001c76a... (10 %)
Writing at 0x00021aed... (14 %)
Writing at 0x0002690b... (17 %)
Writing at 0x0002b1c2... (21 %)
Writing at 0x0002fc69... (25 %)
Writing at 0x000345db... (28 %)
Writing at 0x000391a7... (32 %)
Writing at 0x0003e0f8... (35 %)
Writing at 0x000441cb... (39 %)
Writing at 0x0004a445... (42 %)
Writing at 0x000517ed... (46 %)
Writing at 0x00061f19... (50 %)
Writing at 0x0006bb76... (53 %)
Writing at 0x000711dd... (57 %)
Writing at 0x00076ad3... (60 %)
Writing at 0x0007c67c... (64 %)
Writing at 0x000820e4... (67 %)
Writing at 0x00087fb4... (71 %)
Writing at 0x0008efd5... (75 %)
Writing at 0x00097e97... (78 %)
Writing at 0x000a065c... (82 %)
Writing at 0x000a68aa... (85 %)
Writing at 0x000aea46... (89 %)
Writing at 0x000b4b5c... (92 %)
Writing at 0x000bbe49... (96 %)
Writing at 0x000c2711... (100 %)
Wrote 734592 bytes (444704 compressed) at 0x00010000 in 10.4 seconds (effective 564.0 kbit/s)...
Hash of data verified.

Leaving...
Hard resetting via RTS pin...
Done


```


