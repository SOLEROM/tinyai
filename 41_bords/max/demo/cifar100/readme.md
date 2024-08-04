
## train
ai8x-training
                > train.py

## quantize
ai8x-synthesis

                > quantize.py
    input       best.pth.tar      
    output      best-q.pth.tar

## eval
ai8x-training
                > train.py    --evaluate 
    input       best-q.pth.tar
    *with param  --save-sample
    output  (1)  eval log
            (2)* sample_XXXX.npy 

## yaml
    write cifar10_XXX.yaml  network descriptor


## load
ai8xize:

    input:
    ```
                (1) A quantized checkpoint file
                (2) A YAML description of the network
                (3) A NumPy “pickle”  .npy  file with sample input data
    ```

    output:

```
├── ai85-cifar.launch
├── cnn.c
├── cnn.h
├── log.txt
├── main.c
├── Makefile
├── project.mk
├── sampledata.h
├── sampleoutput.h
├── softmax.c
└── weights.h
```


## make

source env
make

output: 


> ls ./build 
board.d   camera.o  _empty_tmp_file.c  led.d        main.d        max78000.map  pb.d               sccb.d     softmax.o           stdio.d            system_max78000.o  tsc2046.d
board.o   cnn.d     heap.d             led.o        main.o        ov7692.d      pb.o               sccb.o     startup_max78000.d  stdio.o            tft_ssd2119.d      tsc2046.o
camera.d  cnn.o     heap.o             ln_args.txt  max78000.elf  ov7692.o      project_defines.h  softmax.d  startup_max78000.o  system_max78000.d  tft_ssd2119.o


