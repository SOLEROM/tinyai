
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