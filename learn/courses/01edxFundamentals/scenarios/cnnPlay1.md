# play1 cnn

Convolutional Neural Networks (CNNs) play test


```

import tensorflow as tf
mnist = tf.keras.datasets.fashion_mnist
(training_images, training_labels), (val_images, val_labels) = mnist.load_data()
training_images=training_images.reshape(60000, 28, 28, 1)
training_images=training_images / 255.0
val_images=val_images.reshape(10000, 28, 28, 1)
val_images=val_images/255.0
````


* (1) a convolution of layer expects the image dimensions to be fully defined. So a color image will have three channels for red, green, and blue. So it will be something by something by 3. But a monochrome image only has one channel.
* (2) output layer will be 10 neurons as before. It's because we have 10 classes.
* (3) flatten before we get into the DNN.This will occur after the filters have done their job.
* (4) define the convolutional neural network:  2D, because the images have a width and height.
And we'll pass filters across them to change the image to extract features.These filter values will be learned over time!
* (5) Pooling that we described previously is implemented by specifying max pooling as a layer.
  * There are different types of Pooling.There's max, min and average.
  * we'll use max pooling, where we take the largest value from the pool.
* (6)  this is the number of filters to apply to the image at this layer. the filter values are going to be randomly initialized as our Guess.And then, they will be learned over time.
* (7) the size of the filter. we choose filters that we had defined a 3 by 3 filter that multiplied across the current pixel and each of its neighbors.
* (8) the size of the Pool is specified as a parameter, which in this case is a 2 by 2 pool. So we'll be picking one pixel out of four.

by Pooling, we're also reducing the size of our image,helping us to emphasize and summarize the features that we extracted. The convolutional layer had 64 filters in it, which means 64 copies of the image are going to be made. So reducing the size of them will reduce the amount
of data flowing through our network.


```
model = tf.keras.models.Sequential([
                  //4////6////7////                    ///// 1 ////////////////
  tf.keras.layers.Conv2D(64, (3,3), activation='relu', input_shape=(28, 28, 1)),

                  ////5/////////8////
  tf.keras.layers.MaxPooling2D(2, 2),

                  ///4///6////7///
  tf.keras.layers.Conv2D(64, (3,3), activation='relu'),

                  ///5/////////8////
  tf.keras.layers.MaxPooling2D(2,2),


  //////////////// 3 ////////////
  tf.keras.layers.Flatten(),
  tf.keras.layers.Dense(20, activation='relu'),

                    //// 2 ////////
  tf.keras.layers.Dense(10, activation='softmax')
])


````

* see lab 9 lab9_Fashion_MNIST_Convolutions.ipynb
* to see what the model sees : lab10_Fashion_MNIST_sees.ipynb
