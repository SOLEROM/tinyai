# coral on gpu


Reminder, the openCL Coral implementation is for the Vivante GC7000Lite GPU, NOT FOR THE TPU. Notes:

    GC7000Lite local memory is only 32KB, so a scratchpad



## build 

cmake -DCMAKE_C_COMPILER=${ARMCC_PREFIX}gcc \
  -DCMAKE_CXX_COMPILER=${ARMCC_PREFIX}g++ \
  -DCMAKE_C_FLAGS="${ARMCC_FLAGS}" \
  -DCMAKE_CXX_FLAGS="${ARMCC_FLAGS}" \
  -DCMAKE_VERBOSE_MAKEFILE:BOOL=ON \
  -DCMAKE_SYSTEM_NAME=Linux \
  -DCMAKE_SYSTEM_PROCESSOR=aarch64 \
  -DTFLITE_ENABLE_GPU=ON \
  ../tensorflow_src/tensorflow/lite/


## opencl

* imx-gpu-viv

``` 
apt policy imx-gpu-viv
imx-gpu-viv:
  Installed: 6.4.2-2
  Candidate: 6.4.2-2
  Version table:
 *** 6.4.2-2 500
        500 https://mendel-linux.org/apt/eagle-bsp-enterprise eagle/main arm64 Packages
        100 /var/lib/dpkg/status
     6.4.2-1 500
        500 https://mendel-linux.org/apt/eagle-bsp-enterprise eagle/main arm64 Packages



```


sudo apt-get install clinfo opencl-c-headers opencl-clhpp-headers
sudo apt-get install ocl-icd-libopencl1 ocl-icd-dev ocl-icd-opencl-dev
> clinfo
must show:
    Number of platforms                               1



## model 

???

## run

./label_image_gpu --use_gpu=true -m mobilenet_v1_1.0_224_quant.tflite -i   dog1.bmp  -l labels_mobilenet_quant_v1_224.txt       
INFO: Loaded model mobilenet_v1_1.0_224_quant.tflite

???