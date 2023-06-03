
## neurons

In reality, what is referred to as a ‘neuron’ here is simply a function that has two learnable parameters, called a ‘weight’ and a ‘bias’, 
where, the output of the neuron will be:

Output = (Weight * Input) + Bias

When multiple neurons work together in layers, the learned weights and biases across these layers can then have the effect of letting the neural network learn more complex patterns.


## layers type 

* Neural Network that were densely connected to each other - Dense layer type
* Convolutional layers contain filters that can be used to transform data. The values of these filters will be learned in the same way as the parameters in the Dense neuron you saw here. Thus, a network containing them can learn how to transform data effectively. This is especially useful in Computer Vision.
* Recurrent layers learn about the relationships between pieces of data in a sequence. There are many types of recurrent layer, with a popular one called LSTM (Long, Short Term Memory), being particularly effective. Recurrent layers are useful for predicting sequence data (like the weather), or understanding text.


more ???
```
layer types that don’t learn parameters themselves, but which can affect the other layers. These include layers like dropouts, which are used to reduce the density of connection between dense layers to make them more efficient, pooling which can be used to reduce the amount of data flowing through the network to remove unnecessary information, and lambda lambda layers that allow you to execute arbitrary code

```

