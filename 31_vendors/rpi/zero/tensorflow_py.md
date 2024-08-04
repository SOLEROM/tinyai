# python pre build

* deps

```
sudo apt update
sudo apt upgrade 
sudo apt install python3-full git  vim
sudo apt-get install python3-pip


sudo apt-get install libgl1-mesa-glx
```



## swap

``` 
sudo swapoff -a
sudo dd if=/dev/zero of=/swapfile bs=500m count=10
sudo chmod 0644 /swapfile 
sudo mkswap /swapfile
sudo swapon /swapfile
```

## vevn

```
sudo apt install python3-venv
python3 -m venv ~/myvirtualenv
source ~/myvirtualenv/bin/activate
```


## lite

* https://github.com/tensorflow/examples/tree/master/lite/examples/image_classification/raspberry_pi


* https://github.com/tensorflow/examples 

```
git clone https://github.com/tensorflow/examples --depth 1

cd examples/lite/examples/image_classification/raspberry_pi
sh setup.sh
```

## if req list not working:
```
pip install tflite-support argparse numpy opencv-python tflite-support protobuf tflite-runtime
```


```

root@raspberrypi:/home/pi/examples/lite/examples/image_classification/raspberry_pi
.
├── classify.py
├── efficientnet_lite0_edgetpu.tflite
├── efficientnet_lite0.tflite
├── README.md
├── requirements.txt
├── setup.sh
└── test_data
    ├── fox.jpeg
    └── ground_truth.csv
```

## test run

```
cd /home/pi/examples/lite/examples/image_classification/raspberry_pi

python3 classify.py --model efficientnet_lite0.tflite --maxResults 5

```


??

wget https://pypi.org/project/tflite-support/#files

##

install python 3.9 from src

wget https://www.python.org/ftp/python/3.7.2/Python-3.7.2.tar.xz
tar xf Python-3.7.2.tar.xz
cd Python-3.7.2
./configure
make -j 4
sudo make altinstall



## vnevn on 37

python3.7 -m venv ~/myvirtualenv
source ~/myvirtualenv/bin/activate


## support for aarch64 py37

wget https://files.pythonhosted.org/packages/67/40/17b3af8499fc244fe29126d36fc38baaded6d5f5a4b8f36fa18d4aa9e2cf/tflite_support-0.4.4-cp37-cp37m-manylinux2014_aarch64.whl

pip install --upgrade pip
pip install tflite_support-0.4.4-cp37-cp37m-manylinux2014_aarch64.whl 


pip install argparse numpy opencv-python 
protobuf tflite-runtime




python classify.py --model efficientnet_lite0.tflite --maxResults 5

## run 

INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
[ WARN:0@4.446] global cap_v4l.cpp:997 open VIDEOIO(V4L2:/dev/video0): can't open camera by index
[ERROR:0@4.459] global obsensor_uvc_stream_channel.cpp:159 getStreamChannelGroup Camera index out of range