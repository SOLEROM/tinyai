# simple test cifar10

* https://www.cs.toronto.edu/~kriz/cifar.html

## run1

* simple test for 1 epoch

```

/data/tinyai/maxCNN/ai8x-training/train.py --deterministic --epochs 1 --optimizer Adam --lr 0.001 --wd 0 --compress policies/s
chedule-cifar-nas.yaml --model ai85nascifarnet --dataset CIFAR10 --device MAX78000 --batch-size 100 --print-freq 100 --validation-split 0 --use-bias --qat-policy policies/qat_policy_late_cifar.yaml --confusion 


 "args": [
                "--deterministic",
                // "--epochs", "300",
                "--epochs", "1",
                "--optimizer", "Adam",
                "--lr", "0.001",
                "--wd", "0",
                "--compress", "policies/schedule-cifar-nas.yaml",
                "--model", "ai85nascifarnet",
                "--dataset", "CIFAR10",
                "--device", "MAX78000",
                "--batch-size", "100",
                "--print-freq", "100",
                "--validation-split", "0",
                "--use-bias",
                "--qat-policy", "policies/qat_policy_late_cifar.yaml",
                "--confusion"
            ]



Configuring device: MAX78000, simulate=False.
Log file for this run: /data/tinyai/maxCNN/ai8x-training/logs/2024.07.01-150738/2024.07.01-150738.log
WARNING: CUDA hardware acceleration is not available, training will be slow
{'start_epoch': 210, 'weight_bits': 8, 'shift_quantile': 0.995}
Optimizer Type: <class 'torch.optim.adam.Adam'>
Optimizer Args: {'lr': 0.001, 'betas': (0.9, 0.999), 'eps': 1e-08, 'weight_decay': 0.0, 'amsgrad': False}
Files already downloaded and verified
Files already downloaded and verified
Dataset sizes:
        training=50000
        validation=10000
        test=10000
Reading compression schedule from: policies/schedule-cifar-nas.yaml


Training epoch: 50000 samples (100 per mini-batch)
Epoch: [0][  100/  500]    Overall Loss 1.772296    Objective Loss 1.772296                                        LR 0.001000    Time 0.449541    
Epoch: [0][  200/  500]    Overall Loss 1.577215    Objective Loss 1.577215                                        LR 0.001000    Time 0.470790    
Epoch: [0][  300/  500]    Overall Loss 1.449045    Objective Loss 1.449045                                        LR 0.001000    Time 0.481469    
Epoch: [0][  400/  500]    Overall Loss 1.360263    Objective Loss 1.360263                                        LR 0.001000    Time 0.476745    
Epoch: [0][  500/  500]    Overall Loss 1.288190    Objective Loss 1.288190    Top1 64.500000    Top5 96.000000    LR 0.001000    Time 0.472397    
--- validate (epoch=0)-----------
10000 samples (100 per mini-batch)
Epoch: [0][  100/  100]    Loss 0.973547    Top1 65.490000    Top5 96.860000    
==> Top1: 65.490    Top5: 96.860    Loss: 0.974

==> Confusion:
[[765  33 105   9   6   0   2  11  37  32]
 [ 39 862   4   5   2   0   0   1  19  68]
 [ 94   6 621  66  90  33  40  23   6  21]
 [ 36  21 169 437  63 105  96  22  20  31]
 [ 38   2 196  66 547  11  59  70   3   8]
 [ 13  13 103 291  71 418  23  49   7  12]
 [ 15   9 113  67  60   4 710   6   5  11]
 [ 31  12  67  27 124  47   9 638   6  39]
 [177  26  20  17   3   1   2   1 728  25]
 [ 45  76   5   8   6   0   5   7  25 823]]

==> Best [Top1: 65.490   Top5: 96.860   Sparsity:0.00   Params: 301760 on epoch: 0]
Saving checkpoint to: ll/checkpoint.pth.tar
--- test ---------------------
10000 samples (100 per mini-batch)
Test: [  100/  100]    Loss 0.973547    Top1 65.490000    Top5 96.860000    
==> Top1: 65.490    Top5: 96.860    Loss: 0.974

==> Confusion:
[[765  33 105   9   6   0   2  11  37  32]
 [ 39 862   4   5   2   0   0   1  19  68]
 [ 94   6 621  66  90  33  40  23   6  21]
 [ 36  21 169 437  63 105  96  22  20  31]
 [ 38   2 196  66 547  11  59  70   3   8]
 [ 13  13 103 291  71 418  23  49   7  12]
 [ 15   9 113  67  60   4 710   6   5  11]
 [ 31  12  67  27 124  47   9 638   6  39]
 [177  26  20  17   3   1   2   1 728  25]
 [ 45  76   5   8   6   0   5   7  25 823]]

```

* log

```

/data/tinyai/maxCNN/ai8x-training/logs/2024.07.01-150738/2024.07.01-150738.log     
==============================================================================                   
2024-07-01 15:07:38,168 - Log file for this run: /data/tinyai/maxCNN/ai8x-training/logs/2024.07.01-150738/2024.07.01-150738.log
2024-07-01 15:07:38,202 - Optimizer Type: <class 'torch.optim.adam.Adam'>
2024-07-01 15:07:38,203 - Optimizer Args: {'lr': 0.001, 'betas': (0.9, 0.999), 'eps': 1e-08, 'weight_decay': 0.0, 'amsgrad': False}
2024-07-01 15:07:40,048 - Dataset sizes:
        training=50000
        validation=10000
        test=10000
2024-07-01 15:07:40,048 - Reading compression schedule from: policies/schedule-cifar-nas.yaml
2024-07-01 15:07:40,063 - 

2024-07-01 15:07:40,064 - Training epoch: 50000 samples (100 per mini-batch)
2024-07-01 15:08:25,024 - Epoch: [0][  100/  500]    Overall Loss 1.772296    Objective Loss 1.772296                                        LR 0.001000    Time 0.449541    
2024-07-01 15:09:14,234 - Epoch: [0][  200/  500]    Overall Loss 1.577215    Objective Loss 1.577215                                        LR 0.001000    Time 0.470790    
2024-07-01 15:10:04,522 - Epoch: [0][  300/  500]    Overall Loss 1.449045    Objective Loss 1.449045                                        LR 0.001000    Time 0.481469    
2024-07-01 15:10:50,785 - Epoch: [0][  400/  500]    Overall Loss 1.360263    Objective Loss 1.360263                                        LR 0.001000    Time 0.476745    
2024-07-01 15:11:36,291 - Epoch: [0][  500/  500]    Overall Loss 1.288190    Objective Loss 1.288190    Top1 64.500000    Top5 96.000000    LR 0.001000    Time 0.472397    
2024-07-01 15:11:37,029 - --- validate (epoch=0)-----------
2024-07-01 15:11:37,030 - 10000 samples (100 per mini-batch)
2024-07-01 15:11:53,512 - Epoch: [0][  100/  100]    Loss 0.973547    Top1 65.490000    Top5 96.860000    
2024-07-01 15:11:54,233 - ==> Top1: 65.490    Top5: 96.860    Loss: 0.974

2024-07-01 15:11:54,243 - ==> Confusion:
[[765  33 105   9   6   0   2  11  37  32]
 [ 39 862   4   5   2   0   0   1  19  68]
 [ 94   6 621  66  90  33  40  23   6  21]
 [ 36  21 169 437  63 105  96  22  20  31]
 [ 38   2 196  66 547  11  59  70   3   8]
 [ 13  13 103 291  71 418  23  49   7  12]
 [ 15   9 113  67  60   4 710   6   5  11]
 [ 31  12  67  27 124  47   9 638   6  39]
 [177  26  20  17   3   1   2   1 728  25]
 [ 45  76   5   8   6   0   5   7  25 823]]

2024-07-01 15:11:54,254 - ==> Best [Top1: 65.490   Top5: 96.860   Sparsity:0.00   Params: 301760 on epoch: 0]
2024-07-01 15:11:54,255 - Saving checkpoint to: logs/2024.07.01-150738/checkpoint.pth.tar
2024-07-01 15:11:54,287 - --- test ---------------------
2024-07-01 15:11:54,287 - 10000 samples (100 per mini-batch)
2024-07-01 15:12:11,529 - Test: [  100/  100]    Loss 0.973547    Top1 65.490000    Top5 96.860000    
2024-07-01 15:12:12,366 - ==> Top1: 65.490    Top5: 96.860    Loss: 0.974

2024-07-01 15:12:12,367 - ==> Confusion:
[[765  33 105   9   6   0   2  11  37  32]
 [ 39 862   4   5   2   0   0   1  19  68]
 [ 94   6 621  66  90  33  40  23   6  21]
 [ 36  21 169 437  63 105  96  22  20  31]
 [ 38   2 196  66 547  11  59  70   3   8]
 [ 13  13 103 291  71 418  23  49   7  12]
 [ 15   9 113  67  60   4 710   6   5  11]
 [ 31  12  67  27 124  47   9 638   6  39]
 [177  26  20  17   3   1   2   1 728  25]
 [ 45  76   5   8   6   0   5   7  25 823]]
```

## evaluate

* the above was a short train for test ; for the reference full train the eval will be:


```


 "args": [
                "--model", "ai85nascifarnet",
                "--dataset", "CIFAR10",
                "--evaluate",
                "--device", "MAX78000",
                "--exp-load-weights-from", "../ai8x-synthesis/trained/ai85-cifar10-qat8-q.pth.tar",
                "-8",
                "--use-bias"
            ]




WARNING: CUDA hardware acceleration is not available, training will be slow
{'start_epoch': 10, 'weight_bits': 8}
=> loading checkpoint ../ai8x-synthesis/trained/ai85-cifar10-qat8-q.pth.tar
=> Checkpoint contents:
+----------------------+-------------+-----------------+
| Key                  | Type        | Value           |
|----------------------+-------------+-----------------|
| arch                 | str         | ai85nascifarnet |
| compression_sched    | dict        |                 |
| epoch                | int         | 243             |
| extras               | dict        |                 |
| optimizer_state_dict | dict        |                 |
| optimizer_type       | type        | Adam            |
| state_dict           | OrderedDict |                 |
+----------------------+-------------+-----------------+

=> Checkpoint['extras'] contents:
+-----------------+--------+---------------+
| Key             | Type   | Value         |
|-----------------+--------+---------------|
| best_epoch      | int    | 243           |
| best_top1       | float  | 90.03         |
| clipping_method | str    | MAX_BIT_SHIFT |
| current_top1    | float  | 90.03         |
+-----------------+--------+---------------+

Loaded compression schedule from checkpoint (epoch 243)
=> loaded 'state_dict' from checkpoint '../ai8x-synthesis/trained/ai85-cifar10-qat8-q.pth.tar'
Optimizer Type: <class 'torch.optim.sgd.SGD'>
Optimizer Args: {'lr': 0.1, 'momentum': 0.9, 'dampening': 0, 'weight_decay': 0.0001, 'nesterov': False}
Files already downloaded and verified
Dataset sizes:
        test=10000
--- test ---------------------
10000 samples (256 per mini-batch)
Test: [   10/   40]    Loss 0.316602    Top1 89.648438    Top5 99.570312    
Test: [   20/   40]    Loss 0.304272    Top1 90.390625    Top5 99.589844    
Test: [   30/   40]    Loss 0.306222    Top1 89.973958    Top5 99.596354    
Test: [   40/   40]    Loss 0.295907    Top1 90.020000    Top5 99.620000    
==> Top1: 90.020    Top5: 99.620    Loss: 0.296


2024-07-01 15:56:31,180 - Log file for this run: /data/tinyai/maxCNN/ai8x-training/logs/2024.07.01-155611/2024.07.01-155611.log
```


Since training can take a significant amount of time, the training script does not overwrite any weights 
previously produced. Results are placed in sub-directories under  logs/  named with the date and time when 
training began. The latest results are always soft-linked to by  latest-log_dir  and  latest_log_file .


```
ls latest_log_dir -la 
lrwxrwxrwx 1 vlad vlad 22 Jul  1 15:56 latest_log_dir -> logs/2024.07.01-155611


```
