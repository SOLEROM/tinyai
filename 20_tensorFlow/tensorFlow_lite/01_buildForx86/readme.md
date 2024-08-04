# build for x86


* in chroot env (x86)

```
sudo apt-get install cmake
sudo apt-get install build-essential

git clone https://github.com/tensorflow/tensorflow.git tensorflow_src

cmake ../tensorflow_src/tensorflow/lite

cmake --build . -j

```


## build

* tree 

```
tflite_build/
|-- CMakeCache.txt
|-- CMakeFiles
|-- FP16
|-- FP16-download
|-- FP16-source
|-- FXdiv
|-- FXdiv-download
|-- FXdiv-source
|-- Makefile
|-- _deps
|-- abseil-cpp
|-- buildtests.sh
|-- check.sh
|-- cmake_install.cmake
|-- compile_commands.json
|-- cpuinfo
|-- debug.sh
|-- eigen
|-- examples
|-- farmhash
|-- fft2d
|-- flatbuffers
|-- flatbuffers-flatc
|-- gemmlowp
|-- libtensorflow-lite.a
|-- ml_dtypes
|-- neon2sse
|-- psimd
|-- psimd-download
|-- psimd-source
|-- pthreadpool
|-- pthreadpool-download
|-- pthreadpool-source
|-- release.sh
|-- ruy
|-- src
|-- tmp
|-- tools
`-- xnnpack


```