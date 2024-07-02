## eval

* run on "-q" file pth;

```

python train.py --model ai85nascifarnet --dataset CIFAR10 --evaluate --device MAX78000 --exp-load-weights-from /data/tinyai/maxCNN/ai8x-training/logs/2024.07.01-150738/best-q.pth.tar -8 --use-bias


```

```
Log file for this run: /data/tinyai/maxCNN/ai8x-training/logs/2024.07.02-083105/2024.07.02-083105.log
WARNING: CUDA hardware acceleration is not available, training will be slow
{'start_epoch': 10, 'weight_bits': 8}
=> loading checkpoint /data/tinyai/maxCNN/ai8x-training/logs/2024.07.01-150738/best-q.pth.tar
=> Checkpoint contents:
+----------------------+-------------+-----------------+
| Key                  | Type        | Value           |
|----------------------+-------------+-----------------|
| arch                 | str         | ai85nascifarnet |
| compression_sched    | dict        |                 |
| epoch                | int         | 0               |
| extras               | dict        |                 |
| optimizer_state_dict | dict        |                 |
| optimizer_type       | type        | Adam            |
| state_dict           | OrderedDict |                 |
+----------------------+-------------+-----------------+

=> Checkpoint['extras'] contents:
+-----------------+--------+-------------------+
| Key             | Type   | Value             |
|-----------------+--------+-------------------|
| best_epoch      | int    | 0                 |
| best_mAP        | int    | 0                 |
| best_top1       | float  | 65.49000000000001 |
| clipping_method | str    | MAX_BIT_SHIFT     |
| current_mAP     | int    | 0                 |
| current_top1    | float  | 65.49000000000001 |
+-----------------+--------+-------------------+

Loaded compression schedule from checkpoint (epoch 0)
=> loaded 'state_dict' from checkpoint '/data/tinyai/maxCNN/ai8x-training/logs/2024.07.01-150738/best-q.pth.tar'
Optimizer Type: <class 'torch.optim.sgd.SGD'>
Optimizer Args: {'lr': 0.1, 'momentum': 0.9, 'dampening': 0, 'weight_decay': 0.0001, 'nesterov': False}
Files already downloaded and verified
Dataset sizes:
        test=10000
--- test ---------------------
10000 samples (256 per mini-batch)
Test: [   10/   40]    Loss 4.170468    Top1 11.406250    Top5 51.835937    
Test: [   20/   40]    Loss 4.155522    Top1 11.503906    Top5 52.031250    
Test: [   30/   40]    Loss 4.187863    Top1 11.523438    Top5 51.432292    
Test: [   40/   40]    Loss 4.203159    Top1 11.460000    Top5 51.150000    
==> Top1: 11.460    Top5: 51.150    Loss: 4.203


Log file for this run: /data/tinyai/maxCNN/ai8x-training/logs/2024.07.02-083105/2024.07.02-083105.log

```