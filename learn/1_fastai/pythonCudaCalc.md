


## matrix mult

* matrix multiplication is represented with the @ operator

```
def linear1(xb): return xb@weights + bias

```

## list comprehension

* for predictions and targets calc in CUDA speed
* how distant each prediction is from 1 if it should be 1, and how distant it is from 0 if it should be 0, and then it will take the mean of all those distances.

```
def mnist_loss(predictions, targets):
    return torch.where(targets==1, 1-predictions, predictions).mean()
```

same as no speed:

```
list comprehension:
 [b[i] if a[i] else c[i] for i in range(len(a))]
```


## Sigmoid

* always outputs a number between 0 and 1
*  it takes any input value, positive or negative, and smooshes it onto an output value between 0 and 1

```
def sigmoid(x): return 1/(1+torch.exp(-x))
```


