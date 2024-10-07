# timercam

## ESP32 PSRAM Timer Camera Fisheye 

https://shop.m5stack.com/products/esp32-psram-timer-camera-fisheye-ov3660

* ESP32-D0WDQ6-V3 with 8M PSRAM and 4M Flash on board. 
* 3.0 megapixel camera (OV3660) with DFOV 120° 
* maximum resolution of 2048x1536 photos 
* supports Wi-Fi image transfer and USB port debugging
* battery 	270mAh

### projects

With a full charged battery, I managed to take 1 picture every 30mn, each time sent through HTTP to my server, for about 6 hours


add it as board in platformio and developed a low power mqtt lapse camera that lasts more than a week sending one image every 5 min
https://github.com/ESP32Home/timercam_mqtt

