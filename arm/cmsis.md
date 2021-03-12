# cmsis

* https://blog.tensorflow.org/2021/02/accelerated-inference-on-arm-microcontrollers-with-tensorflow-lite.html?m=1

```
Arm’s open source CMSIS-NN library provides optimized implementations of common neural network functions that maximize performance on Cortex-M processors. This includes making use of DSP and M-Profile Vector Extension (MVE) instructions for hardware acceleration of operations such as matrix multiplication. 

The Arm Cortex-M4 processor supports DSP extensions, that enables the processor to execute DSP-like instructions for faster inference.

```

## test

```
For example, to build the person detection example for the SparkFun Edge with CMSIS-NN kernels, you can use the following command:

make -f tensorflow/lite/micro/tools/make/Makefile TARGET=sparkfun_edge OPTIMIZED_KERNEL_DIR=cmsis_nn person_detection_int8_bin

```

