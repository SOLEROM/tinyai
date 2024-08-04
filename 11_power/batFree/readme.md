# battery-free

* battery-free AI and edge computing. 

## energy sources

Energy Harvesting

* Solar Power: Utilizing solar cells to convert light into electrical energy, which can power AI devices.
* Thermal Energy: Harvesting energy from temperature gradients or body heat.
* Kinetic Energy: Capturing energy from motion, such as vibrations or human movement.
* RF Energy: Collecting energy from ambient radio frequency signals (Wi-Fi, cellular networks).


## Power Management Strategies

* Duty Cycling: Activating the AI processor only when necessary and keeping it in a low-power state otherwise.
* Event-Driven Processing: Triggering computations based on specific events or conditions rather than continuous monitoring.
* Adaptive Sampling: Dynamically adjusting the sampling rate of sensors based on the context to save energy.

## Efficient AI Algorithms

* Quantized Neural Networks: Reducing the precision of neural network weights and activations to lower computational demands.
* Binary Neural Networks: Using binary weights and activations for extremely low-power inference (e.g., Xnor.ai's technology).
* Sparse Neural Networks: Exploiting sparsity to minimize the number of computations required.
* Model Compression: Applying techniques like pruning and knowledge distillation to create smaller, more efficient models.

## boards:

### xnor.ai
* [xnor ai (bought by apple)](./XnorAi.md)

### **BrainChip**
- **Technology**: BrainChip focuses on neuromorphic computing, which mimics the neural structures and operation of the human brain. Their Akida Neural Processor is designed for ultra-low-power AI processing.
- **Applications**: Suitable for edge AI applications such as image and video processing, pattern recognition, and anomaly detection in various IoT devices.

### **Ambiq Micro**
- **Technology**: Ambiq Micro's Subthreshold Power Optimized Technology (SPOT) platform enables ultra-low-power processing. They produce microcontrollers and processors that operate at very low power levels.
- **Applications**: Wearables, smart home devices, and other IoT applications where battery life is crucial.

### **Syntiant**
- **Technology**: Syntiant designs ultra-low-power neural decision processors (NDPs) that are specifically optimized for always-on deep learning applications in battery-powered devices.
- **Applications**: Voice and sensor applications in smart speakers, earbuds, hearing aids, and other IoT devices.

### **Eta Compute**
- **Technology**: Eta Compute develops energy-efficient microcontrollers and AI processors designed to operate at extremely low power levels, often leveraging energy harvesting.
- **Applications**: Industrial IoT, health monitoring, smart home devices, and other applications where power efficiency is critical.

### **GreenWaves Technologies**
- **Technology**: GreenWaves Technologies offers the GAP8 processor, an ultra-low-power RISC-V-based processor designed for AI and signal processing in edge devices.
- **Applications**: Audio processing, image recognition, and other AI applications in battery-operated or energy-harvesting devices.

### **DeepX**
- **Technology**: DeepX focuses on developing ultra-low-power AI processors for edge devices, leveraging proprietary algorithms and chip designs to reduce power consumption.
- **Applications**: Smart cameras, wearables, and other IoT devices requiring efficient on-device AI processing.
