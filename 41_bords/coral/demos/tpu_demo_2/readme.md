# demo2

inference on the Edge TPU using the TensorFlow Lite API


##  install 

```bash
mkdir coral && cd coral
git config --global http.sslverify false
git clone https://github.com/google-coral/pycoral.git
cd pycoral
bash examples/install_requirements.sh classify_image.py
```

##  run

```
python3 examples/classify_image.py \
--model test_data/mobilenet_v2_1.0_224_inat_bird_quant_edgetpu.tflite \
--labels test_data/inat_bird_labels.txt \
--input test_data/parrot.jpg

----INFERENCE TIME----
Note: The first inference on Edge TPU is slow because it includes loading the model into Edge TPU memory.
14.1ms
3.8ms
3.7ms
3.4ms
3.4ms
-------RESULTS--------
Ara macao (Scarlet Macaw): 0.75781

```

## inside

* for install_requirements.sh classify_image.py getting:

```
function get_classification() {
  download \
    "mobilenet_v2_1.0_224_inat_bird_quant_edgetpu.tflite" \
    "mobilenet_v2_1.0_224_inat_bird_quant.tflite" \
    "inat_bird_labels.txt" \
    "parrot.jpg"
}

```


* then run examples/classify_image.py

