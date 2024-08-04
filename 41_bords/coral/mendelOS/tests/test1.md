

sudo mount -o loop ./rootfs_converted.raw.img /mnt
sudo DEBIAN_FRONTEND=noninteractive DEBCONF_NONINTERACTIVE_SEEN=true LC_ALL=C LANGUAGE=C LANG=C chroot /mnt /bin/bash



sudo apt install apt-transport-https curl gnupg -y

pip3 install https://dl.google.com/coral/python/tflite_runtime-2.5.0.post1-cp37-cp37m-linux_aarch64.whl
git clone https://github.com/tensorflow/tensorflow.git tensorflow




## Run a model using the TensorFlow Lite API

git clone https://github.com/google-coral/tflite.git
cd tflite/python/examples/classification
bash install_requirements.sh

python3 classify_image.py \
--model models/mobilenet_v2_1.0_224_inat_bird_quant_edgetpu.tflite \
--labels models/inat_bird_labels.txt \
--input images/parrot.jpg