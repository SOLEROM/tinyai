
docker pull tensorflow/tensorflow:devel

docker run -it  tensorflow/tensorflow:devel bash
mkdir -p ${HOME}/toolchains


curl -LO https://developer.arm.com/-/media/Files/downloads/gnu/11.3.rel1/binrel/arm-gnu-toolchain-11.3.rel1-x86_64-arm-none-linux-gnueabihf.tar.xz?rev=65520e9cdf324eca9c02f5302c904fa4&hash=0A1256D118EB7077B4BAA5B2A44FFB72
tar xf arm-gnu-toolchain-11.3.rel1-x86_64-arm-none-linux-gnueabihf.tar.xz\?rev\=65520e9cdf324eca9c02f5302c904fa4 -C ${HOME}/toolchains

cd /tensorflow_src/
git pull 
sudo apt-get install cmake

cd /tensorflow_src/tensorflow
mkdir tflite_build
cd tflite_build

ARMCC_FLAGS="-march=armv7-a -mfpu=neon-vfpv4 -funsafe-math-optimizations -mfp16-format=ieee"

ARMCC_PREFIX=/root/toolchains/arm-gnu-toolchain-11.3.rel1-x86_64-arm-none-linux-gnueabihf/bin/arm-none-linux-gnueabihf-

cmake -DCMAKE_C_COMPILER=${ARMCC_PREFIX}gcc \
  -DCMAKE_CXX_COMPILER=${ARMCC_PREFIX}g++ \
  -DCMAKE_C_FLAGS="${ARMCC_FLAGS}" \
  -DCMAKE_CXX_FLAGS="${ARMCC_FLAGS}" \
  -DCMAKE_VERBOSE_MAKEFILE:BOOL=ON \
  -DCMAKE_SYSTEM_NAME=Linux \
  -DCMAKE_SYSTEM_PROCESSOR=armv7 \
  ../lite/

cmake -DCMAKE_C_COMPILER=${ARMCC_PREFIX}gcc \
  -DCMAKE_CXX_COMPILER=${ARMCC_PREFIX}g++ \
  -DCMAKE_C_FLAGS="${ARMCC_FLAGS}" \
  -DCMAKE_CXX_FLAGS="${ARMCC_FLAGS}" \
  -DCMAKE_VERBOSE_MAKEFILE:BOOL=ON \
  -DCMAKE_SYSTEM_NAME=Linux \
  -DCMAKE_SYSTEM_PROCESSOR=armv7 \
  -DTFLITE_ENABLE_XNNPACK=ON \
  ../lite/

cmake -DCMAKE_C_COMPILER=${ARMCC_PREFIX}gcc \
  -DCMAKE_CXX_COMPILER=${ARMCC_PREFIX}g++ \
  -DCMAKE_C_FLAGS="${ARMCC_FLAGS}" \
  -DCMAKE_CXX_FLAGS="${ARMCC_FLAGS}" \
  -DCMAKE_VERBOSE_MAKEFILE:BOOL=ON \
  -DCMAKE_SYSTEM_NAME=Linux \
  -DCMAKE_SYSTEM_PROCESSOR=armv7 \
  -DTFLITE_ENABLE_XNNPACK=OFF \
  ../lite/



cmake --build . -j -t label_image
cmake --build . -t label_image



https://www.tensorflow.org/install/errors


https://github.com/tensorflow/tensorflow/tree/master/tensorflow/lite/examples/label_image
https://stackoverflow.com/questions/75708825/undefined-reference-error-when-building-tensorflow-lite-image-classification-wit
