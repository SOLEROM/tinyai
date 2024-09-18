


### Adding New Models and New Datasets to the Network Loader

Adding new datasets to the Network Loader is implemented as follows:

1. Provide the [network model](#model), its YAML description and weights. Place the YAML file (e.g., `new.yaml`) in the `networks` directory, and weights in the `trained` directory.
   The non-quantized weights are obtained from a training checkpoint, for example:
   `(ai8x-synthesis) $ cp ../ai8x-training/logs/2020.06.02-154133/best.pth.tar trained/new-unquantized.pth.tar`

2. When using post-training quantization, the quantized weights are the result of the quantization step. Copy and customize an existing quantization shell script, for example:
   `(ai8x-synthesis) $ cp scripts/quantize_mnist.sh scripts/quantize_new.sh`

   Then, *edit this script to point to the new [model](#model) and [dataset](#data-loader)* (`vi scripts/quantize_new.sh`), and call the script to generate the quantized weights. Example:

   ```shell
   (ai8x-synthesis) $ scripts/quantize_new.sh 
   Configuring device: MAX78000.
   Reading networks/new.yaml to configure network...
   Converting checkpoint file trained/new-unquantized.pth.tar to trained/new.pth.tar
   +----------------------+-------------+----------+
   | Key                  | Type        | Value    |
   |----------------------+-------------+----------|
   | arch                 | str         | ai85net5 |
   | compression_sched    | dict        |          |
   | epoch                | int         | 165      |
   | extras               | dict        |          |
   | optimizer_state_dict | dict        |          |
   | optimizer_type       | type        | SGD      |
   | state_dict           | OrderedDict |          |
   +----------------------+-------------+----------+
   Model keys (state_dict):
   conv1.conv2d.weight, conv2.conv2d.weight, conv3.conv2d.weight, conv4.conv2d.weight, fc.linear.weight, fc.linear.bias
   conv1.conv2d.weight avg_max: tensor(0.3100) max: tensor(0.7568) mean: tensor(0.0104) factor: 54.4 bits: 8
   conv2.conv2d.weight avg_max: tensor(0.1843) max: tensor(0.2897) mean: tensor(-0.0063) factor: 108.8 bits: 8
   conv3.conv2d.weight avg_max: tensor(0.1972) max: tensor(0.3065) mean: tensor(-0.0053) factor: 108.8 bits: 8
   conv4.conv2d.weight avg_max: tensor(0.3880) max: tensor(0.5299) mean: tensor(0.0036) factor: 108.8 bits: 8
   fc.linear.weight avg_max: tensor(0.6916) max: tensor(0.9419) mean: tensor(-0.0554) factor: 108.8 bits: 8
   fc.linear.bias   
   ```

3. Provide a sample input. The sample input is used to generate a known-answer test (self test) against the predicted label. The purpose of the sample input is to ensure that the generated code matches the model — it does <u>*not*</u> ensure that the model is of good quality. However, it can help finding issues in the YAML description of the model.

   The sample input is provided as a NumPy “pickle” — add `sample_dset.npy` for the dataset named `dset` to the `tests` directory. This file can be generated by saving a sample in CHW format (no batch dimension) using `numpy.save()`, see below.

   For example, the MNIST 1×28×28 image sample would be stored in `tests/sample_mnist.npy` in an `np.array` with shape `[1, 28, 28]` and datatype `>i8` (`np.int64`). The file can contain random integers, or it can be obtained from the `train.py` software.

   *Note: To convert an existing sample input file to `np.int64`, use the `tests/convert_sample.py` script.*