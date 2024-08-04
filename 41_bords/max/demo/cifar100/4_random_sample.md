# Random Sample Input 

## option1:

grayscale MNIST example:

* The array must be of data type  np.int64
* For RGB image inputs, there are three channels

```
import os
import numpy as np
a = np.random.randint(-128, 127, size=(1, 28, 28), dtype=np.int64)
np.save(os.path.join('tests', 'sample_mnist'), a, allow_pickle=False, 
fix_imports=False)
```

## option2:

* train with save-sample

```


python train.py --model ai85nascifarnet --dataset CIFAR10 --evaluate --device MAX78000 --exp-load-weights-from /data/tinyai/maxCNN/ai8x-training/logs/2024.07.01-150738/best-q.pth.tar -8 --use-bias --save-sample 10

```

will produce => sample_cifar10.npy



