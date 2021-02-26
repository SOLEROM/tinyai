#  ESP-IDF (Espressif IoT Development Framework) 

* install the ESP-IDF framework on your computer (ESP32 SDK for Arduino IDE is not enough)
* https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/index.html


# sw 

* Toolchain to compile code for ESP32
* Build tools - CMake and Ninja to build a full Application for ESP32
* ESP-IDF that essentially contains API (software libraries and source code) for ESP32 and scripts to operate the Toolchain

## install

* Prerequisites

```
sudo apt-get install git wget flex bison gperf python3 python3-pip python3-setuptools cmake ninja-build ccache libffi-dev libssl-dev dfu-util libusb-1.0-0

sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 10

```

* get the code 

```
git clone --recursive https://github.com/espressif/esp-idf.git
```

* Set up the tools . Aside from the ESP-IDF, you also need to install the tools used by ESP-IDF, such as the compiler, debugger, Python packages, etc.

```
cd esp-idf
./install.sh
```

* Set up the environment variables

```
. <installDIR>/esp-idf/export.sh

```




