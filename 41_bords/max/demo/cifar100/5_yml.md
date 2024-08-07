# YAML Network Description


* example cifar10-nas.yaml

```
(ai8x-synthesis) maxCNN/ai8x-synthesis/networks/cifar10-nas.yaml
=================================================================
---
# HWC (little data) configuration for CIFAR10 NAS Model
# Simple Model

arch: ai85nascifarnet
dataset: CIFAR10

layers:
  - out_offset: 0x4000
    processors: 0x0000000000000007  # 1_1
    operation: conv2d
    kernel_size: 3x3
    pad: 1
    activate: ReLU
    data_format: HWC
  - out_offset: 0x0000
    processors: 0xffffffffffffffff  # 1_2
    operation: conv2d
    kernel_size: 1x1
    pad: 0
    activate: ReLU
  - out_offset: 0x4000
    processors: 0x00000000ffffffff  # 1_3
    operation: conv2d
    kernel_size: 3x3
    pad: 1
    activate: ReLU
  - max_pool: 2
    pool_stride: 2
    out_offset: 0x0000
    processors: 0xffffffffffffffff  # 2_1
    operation: conv2d
    kernel_size: 3x3
    pad: 1
    activate: ReLU
  - out_offset: 0x4000
    processors: 0xffffffff00000000  # 2_2
    operation: conv2d
    kernel_size: 1x1
    pad: 0
    activate: ReLU
  - max_pool: 2
    pool_stride: 2
    out_offset: 0x0000
    processors: 0xffffffffffffffff  # 3_1
    operation: conv2d
    kernel_size: 3x3
    pad: 1
    activate: ReLU
  - out_offset: 0x4000
    processors: 0xffffffffffffffff  # 3_2
    operation: conv2d
    kernel_size: 1x1
    pad: 0
    activate: ReLU
  - max_pool: 2
    pool_stride: 2
    out_offset: 0x0000
    processors: 0xffffffffffffffff  # 4_1
    operation: conv2d
    kernel_size: 3x3
    pad: 1
    activate: ReLU
  - out_offset: 0x4000
    processors: 0xffffffffffffffff  # 4_2
    operation: conv2d
    kernel_size: 3x3
    pad: 1
    activate: ReLU
  - max_pool: 2
    pool_stride: 2
    out_offset: 0x0000
    processors: 0xffffffffffffffff  # 5_1
    operation: conv2d
    kernel_size: 1x1
    pad: 0
    activate: ReLU
  - flatten: true
    out_offset: 0x4000
    processors: 0xffffffffffffffff
    operation: MLP
    output_width: 32
    activate: None

```


## check

```
sudo apt-get install yamllint
yamllint networks/cifar10-nas.yaml
```

* if complain about new line, update to unix:

```
.yamllint         
==========


---
extends: default
rules:
  line-length: {max: 1024}
  new-lines:
    type: unix
  new-line-at-end-of-file: enable


```