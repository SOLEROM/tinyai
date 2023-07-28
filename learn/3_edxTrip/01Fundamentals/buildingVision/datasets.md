## TensorFlow Datasets

* https://www.tensorflow.org/datasets

```


pip install tensorflow-datasets

```

```


import tensorflow as tf

import tensorflow_datasets as tfds

mnist_data = tfds.load("fashion_mnist")

for item in mnist_data:

print(item)

```


## Augmentation

* splitting up data into Training, Testing, Validation sets, and Mapping Functions, which allow you to do things like Augmentation


```


def augmentimages(image, label):

  image = tf.cast(image, tf.float32)

  image = (image/255)

  image = tf.image.random_flip_left_right(image)

  return image, label

data = tfds.load('horses_or_humans', split='train', as_supervised=True)

train = data.map(augmentimages)
```

tfds.load is used to get the horses or humans dataset. It’s pre-split into a ‘train’ subset with the training data, so you can request that. Then, once you have data, you can call it’s ‘map’ method, passing it a function like ‘AugmentImages’ as shown, and from within there you can do your image augmentation.