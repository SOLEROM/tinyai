# Linux-based devices with Python


* https://www.tensorflow.org/lite/guide/python

* use TensorFlow Lite interpreter, instead of all TensorFlow packages
* will need a TensorFlow model converted to TensorFlow Lite. 


## tflite_runtime
The tflite_runtime package is designed for running TensorFlow Lite models on devices with limited resources, and it may not include the full set of features available in the 
standard TensorFlow library, including GPU support.

## full version

``````
# Requires the latest pip
pip install --upgrade pip

# Current stable release for CPU and GPU
<!-- pip install tensorflow -->
python3 -m pip install tensorflow
python3 -m pip install tensorflow-io

mendel@mocha-finch:~$ sudo pip3 install --upgrade --force-reinstall tensorflow-io tensorflow


```


