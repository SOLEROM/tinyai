# 1 def factory boot

* https://i1.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/12/ESP32-CAM-FTDI-programmer-5V-supply.png?w=750&quality=100&strip=all&ssl=1


```
 boot: Defaulting to factory image
I (114) esp_image: segment 0: paddr=0x00010020 vaddr=0x3f400020 size=0x17178 ( 94584) map
I (156) esp_image: segment 1: paddr=0x000271a0 vaddr=0x3ffb0000 size=0x031d8 ( 12760) load
I (161) esp_imagesegment 2: paddr=0x0002a380 vaddr=0x40080000 size=0x00400 (  1024) load
I (163) esp_image: segment 3: paddr=0x0002avaddr=0x40080400 size=0x05888 ( 22664) load
I (181) esp_image: segment 4: paddr=0x00030018 vaddr=0x400d0018 size=0xf0 (457968) map
I (340) esp_image: segment 5: paddr=0x0009fd10 vaddr=0x40085c88 size=0x053e0 ( 21472) load
I (349) esp_imagesegment 6: paddr=0x000a50f8 vaddr=0x400c0000 size=0x00000 (     0) load
I (356) boot: Loaded app from partition at et 0x10000
I (356) boot: Disabling RNG early entropy source...
I (361) cpu_start: Pro cpu up.
364) cpu_start: Starting app cpu, entry point is 0x4008122c
I (356) cpu_start: App cpu up.
I (375) heap_init: Initializing. RAM available for dynamic allocation:
I (382) heap_init: At 3FFAE6E0 l 00001920 (6 KiB): DRAM
I (388) heap_init: At 3FFB9980 len 00026680 (153 KiB): DRAM
I (394) heap_init: 3FFE0440 len 00003BC0 (14 KiB): D/IRAM
I (400) heap_init: At 3FFE4350 len 0001BCB0 (111 KiB): D/IRAM
I  heap_init: At 4008B068 len 00014F98 (83 KiB): IRAM
I (413) cpu_start: Pro cpu start user code
ets Jun  8 2016 00:22:57

rst:0xc (SW_CPU_RESET),boot:0x13 (SPI_FAST_FLASH_BOOT)
configsip: 0, SPIWP:0xee
clk_drv:0x_drv:0x00,d_drv:0x00,cs0_drv:0x00,hd_drv:0x00,wp_drv:0x00
mode:DIO, clock div:2
load:0x3fff0018,len:4
load:0x3fff001c,len:56oad:0x40078000,len:0
ho 12 tail 0 room 4
load:0x40078000,len:13920
entry 0x40078fd8
I (30) boot: ESP-IDF v3.1-dev-46eae33a-dirty 2nd stage bootloader
I (30) boot: compile time 10:52:13
I (32) boot: Enabling RNG early entropy source...
I (37) boot: SPI Speed      : 40MHz
I (41) boot: SPI Mode     : DIO
I (45) boot: SPI Flash Size : 4MB
I (49) boot: Partition Table:
I (53) boot: ## Labe            Usage          Type ST Offset   Length
I (60) boot:  0 nvs              WiFi data        01 02 00+-----------------------------+
I (68) boot:  1 otadata          OTA data         01 00 00|                             |
I (75) boot:  2 phy_init         RF data          01 01 00|  Cannot open /dev/ttyUSB3!  |
I (83) boot:  3 factory          factory app     00 00 000|                             |
I (90) boot:  4 ota_0            OTA app          00 10 00+-----------------------------+
Iot:  5 ota_1            OTA app          00 11 00210000 00100000
I (105) boot: End of partition table
Ioot: Defaulting to factory image



```
