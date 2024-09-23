# metrics


### 1. **TOPS/W (Tera Operations Per Second per Watt):**
   - **Definition:** This metric measures the computational performance (TOPS) relative to the power consumption (Watt).

     $$
     \text{TOPS/W} = \frac{\text{TOPS}}{\text{Power Consumption (W)}}
     $$


### 2. **Power Efficiency (Images/Watt):**
   - **Definition:** The number of images or data points the module can process per watt.
   
     $$
     \text{Images/Watt} = \frac{\text{FPS}}{\text{Power Consumption (W)}}
     $$



### 3. **"Inference Efficiency Score" (IES)**. 
This metric will give you an idea of how well the module balances computational power, efficiency, and real-time performance.


$$
\text{IES} = \frac{\text{FPS} \times \text{TOPS/W}}{\text{Nominal Power Consumption}}
$$

Where:
- **FPS**: Frames Per Second, indicating the module’s real-time performance for a specific model.
- **TOPS/W**: Tera Operations Per Second per Watt, indicating computational efficiency.
- **Nominal Power Consumption**: Average power consumption in watts during inference (to normalize the metric).





### 4. **AI Capability Index (ACI)**.


To integrate frame rate (FPS) into the AI Capability Index, we can define a new metric:

$$
\text{ACI}_{\text{FPS}} = \frac{\text{FPS} \times \text{TOPS/W} \times \text{Utilization Factor}}{1 + \left( \frac{\text{Power Consumption}}{\text{Max Power Capacity}} \right)}
$$

Where:
- **FPS**: Frames per second the module can achieve for a specific model.
- **TOPS/W**: Represents power efficiency.
- **Utilization Factor**: Represents how much of the computational capacity is being utilized.
- **Power Consumption**: Actual power consumption of the module during operation.
- **Max Power Capacity**: Maximum power the module can handle safely.



## example of Power Bank calc

   The capacity of a power bank is usually given in milliampere-hours (mAh) and the voltage it provides (typically 5V for USB output). 

   $$
   \text{Total Energy} (Wh) = \frac{\text{Capacity (mAh)} \times \text{Voltage (V)}}{1000}
   $$

   For example, if you have a 10,000 mAh power bank with a 5V output:

   $$
   \text{Total Energy} = \frac{10000 \times 5}{1000} = 50 \text{Wh}
   $$

### **Calculate Power Consumption of the Board:**
   Measure or estimate the power consumption of your board in watts (W).

   For example, if your board consumes 2W during operation.

### **Calculate the Operating Time:**
   You can now calculate how long the power bank will last with your board.

   $$
   \text{Operating Time (hours)} = \frac{\text{Total Energy (Wh)}}{\text{Power Consumption (W)}}
   $$

   Using the values from above:

   $$
   \text{Operating Time} = \frac{50}{2} = 25 \text{ hours}
   $$

### **Calculate Board Efficiency:**
   You can define the board's efficiency in terms of how much useful computation you get per unit of energy provided by the power bank. Using the Inference Efficiency Score (IES) from before, you can calculate:

   $$
   \text{Board Efficiency (IES per Wh)} = \frac{\text{Inference Efficiency Score (IES)}}{\text{Total Energy (Wh)}}
   $$

   For the example IES of 195 and Total Energy of 50 Wh:

   $$
   \text{Board Efficiency} = \frac{195}{50} = 3.9 \text{ IES per Wh}
   $$

