# espWHO

* https://robotzero.one/esp32-camera-module/

```
(container) 
git clone --recursive https://github.com/espressif/esp-who.git
```

```
cd <proj>/esp-who/examples/single_chip/camera_web_server/
make menuconfig

Serial flasher config —> Default serial port (Change to the port number shown in Device Manager – ie COM3)
Camera Web Server —> WiFi Settings —> (Add your WiFi SSID and Password)
Camera Web Server —> Camera Pins —> Select Camera Pinout —> (Select ESP32-CAM by AI-Thinker)
Component config —> ESP32-specific —> SPI Ram config —> Type of SPI RAM chip (Select Auto-detect)


```

```
make flash

//after power cycle
make monitor
//get the ip to monitor
```
