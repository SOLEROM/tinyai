# connectors: 

## RPI
* https://www.arducam.com/raspberry-pi-camera-pinout/

## esp32cam
* FPC connector
* cams:
  * ov7670
  * ov2640 jpeg
  
```
Espressif Systems ESP32 has many new interfaces over ESP8266, but still lacks a hardware camera interface like DVP or MIPI CSI. However, it’s still possible to connect a camera to the I2S interface. What? Isn’t I2S used for audio? It turns out there’s more to ESP32’s “I2S  interface” as pointed out in the forums:

    The I2S subsystem in the ESP32 also provides a high speed bus connected directly to RAM for Direct Memory Access. Putting it simply, you can configure the ESP32 I2S subsystem to send or receive parallel data under hardware control.

```

## ECM3532
* 1 x Camera: Himax HM0360


## Apollo3
* Himax HM01B0 camera connector
* 


## HM01B0
* vidoe data:  8-bit, 4-bit, 1-bit data output FVLD, LVLD, PCL

## HM0360
* 

## ARX3A0
* MIPI interface


## nxp rt1064 
* The i.MX RT1052 and RT1064 boards have a 24pin connector
* i.MX RT1060 Camera Interfaces : Parallel

