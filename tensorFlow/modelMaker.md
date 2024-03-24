# model Maker

 TensorFlow Lite Model Maker library simplifies the process of training a TensorFlow Lite model using custom dataset.


## install


pip install tflite-model-maker

## example

Model Maker allows you to train a TensorFlow Lite model using custom datasets in just a few lines of code. For example, here are the steps to train an image classification model.

```
from tflite_model_maker import image_classifier
from tflite_model_maker.image_classifier import DataLoader

# Load input data specific to an on-device ML app.
data = DataLoader.from_folder('flower_photos/')
train_data, test_data = data.split(0.9)

# Customize the TensorFlow model.
model = image_classifier.create(train_data)

# Evaluate the model.
loss, accuracy = model.evaluate(test_data)

# Export to Tensorflow Lite model and label file in `export_dir`.
model.export(export_dir='/tmp/')

```