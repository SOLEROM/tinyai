

## about

https://www.tensorflow.org/lite/examples/image_classification/overview



## build


cmake --build . -j -t label_image

file examples/label_image/label_image 
examples/label_image/label_image: ELF 64-bit LSB shared object, x86-64, version

wget https://storage.googleapis.com/download.tensorflow.org/models/tflite/mobilenet_v1_1.0_224_quant_and_labels.zip



convert dog1.jpg -type truecolor dog1.bmp
./label_image -m models/mobilenet_v1_1.0_224_quant.tflite -i  dog1.bmp -l models/labels_mobilenet_quant_v1_224.txt -x 1


```
INFO: Loaded model models/mobilenet_v1_1.0_224_quant.tflite
INFO: resolved reporter
INFO: Initialized TensorFlow Lite runtime.
INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
INFO: XNNPACK delegate created.
INFO: Use xnnpack: [1]
VERBOSE: Replacing 29 out of 31 node(s) with delegate (TfLiteXNNPackDelegate) node, yielding 4 partitions for the whole graph.
INFO: Applied XNNPACK delegate.
INFO: Applying 1 TensorFlow Lite delegate(s) lazily.
INFO: Successfully applied the default TensorFlow Lite delegate indexed at 0.
 *NOTE*: because a delegate has been applied, the precision of computations should be unchanged, but the exact output tensor values may have changed. If such output values are checked in your code, like in your tests etc., please consider increasing error tolerance for the check.
INFO: invoked
INFO: average time: 5.323 ms
INFO: 0.752941: 204 West Highland white terrier
INFO: 0.0862745: 189 wire-haired fox terrier
INFO: 0.0392157: 200 Scotch terrier
INFO: 0.0392157: 191 Sealyham terrier
INFO: 0.027451: 193 cairn


```