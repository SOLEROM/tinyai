# Quantization

There are two main approaches to quantization — quantization-aware training and post-training quantization.

quantize.py  software quantizes an existing PyTorch checkpoint file and writes out a 
new PyTorch checkpoint file that can then be used to evaluate the quality of the quantized network, using the 
same PyTorch framework used for training. 

The same new quantized checkpoint file will also be used to feed 
the Network Loader.

## --help

```
python quantize.py --help
usage: quantize.py [-h] [-c S] --device N [--clip-method {AVGMAX,MAX,STDDEV,SCALE}] [--qat-weight-bits QAT_WEIGHT_BITS] [-v] [--scale SCALE] [--stddev STDDEV] input output

Checkpoint to MAX78000 Quantization

positional arguments:
  input                 path to the checkpoint file
  output                path to the output file

optional arguments:
  -h, --help            show this help message and exit
  -c S, --config-file S
                        optional YAML configuration file containing layer configuration
  --device N            set device
  --clip-method {AVGMAX,MAX,STDDEV,SCALE}
                        disable quantization-aware training (QAT) information and choose saturation clipping method
  --qat-weight-bits QAT_WEIGHT_BITS
                        override number of weight bits used in QAT
  -v, --verbose         verbose mode
  --scale SCALE         set the scale value for the SCALE method (default: magic 0.85)
  --stddev STDDEV       set the number of standard deviations for the STDDEV method (default: 2.00)

```

## (A) QAT

* Quantization-Aware Training 
* the better performing approach.
* enabled by default.


The input checkpoint to  quantize.py  is either  qat_best.pth.tar , the best QAT epoch’s checkpoint, or qat_checkpoint.pth.tar , the final QAT epoch’s checkpoint.


```
(ai8x-synthesis) $ python quantize.py proj/qat_best.pth.tar proj/proj_q8.pth.tar --device MAX78000
```


## (B) Post-Training Quantization

* should be used when  --qat-policy None  is specified for training
* “optimum” scale factor for simple clipping is highly dependent on the model and weight data.

```
(ai8x-synthesis) $ python quantize.py proj2/best.pth.tar proj2/proj2_q8.pth.tar --device MAX78000 --scale 0.85 --clip-method SCALE

```


## test

```

(ai8x-synthesis) (venv) (base) (main)vlad@vladis:maxCNN/ai8x-synthesis ‹main›$ python quantize.py /data/tinyai/maxCNN/ai8x-training/logs/2024.07.01-150738/best.pth.tar /data/tinyai/maxCNN/ai8x-training/logs/2024.07.01-150738/best-q.pth.tar --device MAX78000 -v


Configuring device: MAX78000
Converting checkpoint file /data/tinyai/maxCNN/ai8x-training/logs/2024.07.01-150738/best.pth.tar to /data/tinyai/maxCNN/ai8x-training/logs/2024.07.01-150738/best-q.pth.tar

Model keys (state_dict):
conv1_1.output_shift, conv1_1.weight_bits, conv1_1.bias_bits, conv1_1.quantize_activation, conv1_1.adjust_output_shift, conv1_1.shift_quantile, conv1_1.op.weight, conv1_1.op.bias, conv1_1.bn.running_mean, conv1_1.bn.running_var, conv1_1.bn.num_batches_tracked, conv1_2.output_shift, conv1_2.weight_bits, conv1_2.bias_bits, conv1_2.quantize_activation, conv1_2.adjust_output_shift, conv1_2.shift_quantile, conv1_2.op.weight, conv1_2.op.bias, conv1_2.bn.running_mean, conv1_2.bn.running_var, conv1_2.bn.num_batches_tracked, conv1_3.output_shift, conv1_3.weight_bits, conv1_3.bias_bits, conv1_3.quantize_activation, conv1_3.adjust_output_shift, conv1_3.shift_quantile, conv1_3.op.weight, conv1_3.op.bias, conv1_3.bn.running_mean, conv1_3.bn.running_var, conv1_3.bn.num_batches_tracked, conv2_1.output_shift, conv2_1.weight_bits, conv2_1.bias_bits, conv2_1.quantize_activation, conv2_1.adjust_output_shift, conv2_1.shift_quantile, conv2_1.op.weight, conv2_1.op.bias, conv2_1.bn.running_mean, conv2_1.bn.running_var, conv2_1.bn.num_batches_tracked, conv2_2.output_shift, conv2_2.weight_bits, conv2_2.bias_bits, conv2_2.quantize_activation, conv2_2.adjust_output_shift, conv2_2.shift_quantile, conv2_2.op.weight, conv2_2.op.bias, conv2_2.bn.running_mean, conv2_2.bn.running_var, conv2_2.bn.num_batches_tracked, conv3_1.output_shift, conv3_1.weight_bits, conv3_1.bias_bits, conv3_1.quantize_activation, conv3_1.adjust_output_shift, conv3_1.shift_quantile, conv3_1.op.weight, conv3_1.op.bias, conv3_1.bn.running_mean, conv3_1.bn.running_var, conv3_1.bn.num_batches_tracked, conv3_2.output_shift, conv3_2.weight_bits, conv3_2.bias_bits, conv3_2.quantize_activation, conv3_2.adjust_output_shift, conv3_2.shift_quantile, conv3_2.op.weight, conv3_2.op.bias, conv3_2.bn.running_mean, conv3_2.bn.running_var, conv3_2.bn.num_batches_tracked, conv4_1.output_shift, conv4_1.weight_bits, conv4_1.bias_bits, conv4_1.quantize_activation, conv4_1.adjust_output_shift, conv4_1.shift_quantile, conv4_1.op.weight, conv4_1.op.bias, conv4_1.bn.running_mean, conv4_1.bn.running_var, conv4_1.bn.num_batches_tracked, conv4_2.output_shift, conv4_2.weight_bits, conv4_2.bias_bits, conv4_2.quantize_activation, conv4_2.adjust_output_shift, conv4_2.shift_quantile, conv4_2.op.weight, conv4_2.op.bias, conv4_2.bn.running_mean, conv4_2.bn.running_var, conv4_2.bn.num_batches_tracked, conv5_1.output_shift, conv5_1.weight_bits, conv5_1.bias_bits, conv5_1.quantize_activation, conv5_1.adjust_output_shift, conv5_1.shift_quantile, conv5_1.op.weight, conv5_1.op.bias, conv5_1.bn.running_mean, conv5_1.bn.running_var, conv5_1.bn.num_batches_tracked, fc.output_shift, fc.weight_bits, fc.bias_bits, fc.quantize_activation, fc.adjust_output_shift, fc.shift_quantile, fc.op.weight, fc.op.bias
conv1_1.op.weight avg_max: 0.19581217 max: 0.25818345 mean: -0.0010339859 factor: [256.] bits: 8
conv1_1.op.bias avg_max: 0.008350415 max: 0.20695026 mean: 0.008350415 factor: [256.] bits: 8
conv1_2.op.weight avg_max: 0.15837905 max: 0.2260818 mean: -0.007221074 factor: [512.] bits: 8
conv1_2.op.bias avg_max: 0.021599323 max: 0.13941085 mean: 0.021599323 factor: [512.] bits: 8
conv1_3.op.weight avg_max: 0.10185581 max: 0.12802085 mean: -0.0012000235 factor: [512.] bits: 8
conv1_3.op.bias avg_max: 0.0047757383 max: 0.104352094 mean: -0.0047757383 factor: [512.] bits: 8
conv2_1.op.weight avg_max: 0.09950264 max: 0.14326133 mean: -0.00075862225 factor: [512.] bits: 8
conv2_1.op.bias avg_max: 0.004228739 max: 0.051477145 mean: -0.004228739 factor: [512.] bits: 8
conv2_2.op.weight avg_max: 0.18644921 max: 0.22853813 mean: -0.0044154814 factor: [512.] bits: 8
conv2_2.op.bias avg_max: 0.0026578833 max: 0.19792882 mean: -0.0026578833 factor: [512.] bits: 8
conv3_1.op.weight avg_max: 0.093789354 max: 0.124638736 mean: 0.000245763 factor: [1024.] bits: 8
conv3_1.op.bias avg_max: 0.001594298 max: 0.057827115 mean: -0.001594298 factor: [1024.] bits: 8
conv3_2.op.weight avg_max: 0.12302495 max: 0.16514893 mean: -0.0025607832 factor: [512.] bits: 8
conv3_2.op.bias avg_max: 0.0038889719 max: 0.14092705 mean: -0.0038889719 factor: [512.] bits: 8
conv4_1.op.weight avg_max: 0.0900123 max: 0.14981413 mean: 0.00013569098 factor: [512.] bits: 8
conv4_1.op.bias avg_max: 0.0013422337 max: 0.037608754 mean: 0.0013422337 factor: [512.] bits: 8
conv4_2.op.weight avg_max: 0.09779563 max: 0.14253432 mean: -0.0007492429 factor: [512.] bits: 8
conv4_2.op.bias avg_max: 0.002731392 max: 0.05317087 mean: -0.002731392 factor: [512.] bits: 8
conv5_1.op.weight avg_max: 0.12837607 max: 0.18337771 mean: 0.0004593544 factor: [512.] bits: 8
conv5_1.op.bias avg_max: 0.008161348 max: 0.08945797 mean: 0.008161348 factor: [512.] bits: 8
fc.op.weight avg_max: 0.17802887 max: 0.20887798 mean: -0.017725335 factor: [512.] bits: 8
fc.op.bias avg_max: 9.30544e-05 max: 0.05948845 mean: 9.30544e-05 factor: [512.] bits: 8