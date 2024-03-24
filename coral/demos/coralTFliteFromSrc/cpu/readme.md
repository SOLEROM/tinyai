# coral on cpu

## app build 

ARMCC_FLAGS="-funsafe-math-optimizations"
cmake -DCMAKE_C_COMPILER=${ARMCC_PREFIX}gcc \
  -DCMAKE_CXX_COMPILER=${ARMCC_PREFIX}g++ \
  -DCMAKE_C_FLAGS="${ARMCC_FLAGS}" \
  -DCMAKE_CXX_FLAGS="${ARMCC_FLAGS}" \
  -DCMAKE_VERBOSE_MAKEFILE:BOOL=ON \
  -DCMAKE_SYSTEM_NAME=Linux \
  -DCMAKE_SYSTEM_PROCESSOR=aarch64 \
  ../tensorflow_src/tensorflow/lite/



## model 

wget https://storage.googleapis.com/download.tensorflow.org/models/tflite/mobilenet_v1_1.0_224_quant_and_labels.zip


## run

* on [coral in chroot](../../../armChrootEnv/readme.md)

```
silly-finch:/# ./label_image -m mobilenet_v1_1.0_224_quant.tflite -i   dog1.bmp  -l labels_mobilenet_quant_v1_224.txt  --accelerated 1
WARN: NNAPI delegate execution provider isn't linked or NNAPI delegate isn't supported on the platform!
INFO: Loaded model mobilenet_v1_1.0_224_quant.tflite
INFO: resolved reporter
INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
INFO: invoked
INFO: average time: 37.26 ms
INFO: 0.772549: 204 West Highland white terrier
INFO: 0.0745098: 189 wire-haired fox terrier
INFO: 0.0392157: 200 Scotch terrier
INFO: 0.0313726: 191 Sealyham terrier
INFO: 0.027451: 193 cairn
```
