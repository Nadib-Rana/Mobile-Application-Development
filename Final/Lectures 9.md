# Sensor 
Sensors are devices that detect and measure physical phenomena and convert them into data for analysis. They are broadly categorized based on what they measure or their application. Here are the 
**3 major categories of sensors**:
---

### 1. **Motion Sensors**  
   - Detect movement, speed, or acceleration.  
   - **Examples**:  
     - Accelerometer  
     - Gyroscope  
     - Gravity 

### 2. **Environmental Sensors**  
   - Measure environmental factors like temperature, humidity, or pressure.  
   - **Examples**:  
     - Temperature Sensor  
     - Humidity Sensor  
     - Barometer  
     - Gas Sensor 

### 3. **Position**    
   - **Examples**:  
     - Magnetometer (compass)  
     - Proximity 

---

**hardware** and **software sensors**:  

### **Hardware Sensors**  
- **Physical components** in a device that directly measure real-world data.  
- Example: Accelerometer (measures motion), Gyroscope (measures rotation), Proximity Sensor (detects nearby objects).  
- Found inside the device and interact with the environment.  

### **Software Sensors**  
- **Virtual sensors** created by combining or processing data from hardware sensors using software.  
- Example: Orientation Sensor (combines accelerometer and gyroscope), Step Counter (uses accelerometer data).  
- They don’t physically exist but mimic functionality.  

In short:  
- **Hardware sensors** = Actual device parts.  
- **Software sensors** = Virtual, rely on hardware data and algorithms.  

##  **sensor names** and their **uses**:

| **Sensor Name**        | **Use**                                                                 |
|-------------------------|-------------------------------------------------------------------------|
| **Accelerometer**       | Detects motion, tilt, shake, and orientation.                          |
| **Gyroscope**           | Measures rotation and angular movement (e.g., gaming, AR/VR).         |
| **Proximity Sensor**    | Detects nearby objects (e.g., turning off the screen during a call).   |
| **Ambient Light Sensor**| Adjusts screen brightness based on surrounding light.                 |
| **Magnetometer**        | Acts as a compass to detect direction.                                |
| **Barometer**           | Measures air pressure for altitude and weather apps.                 |
| **GPS**                 | Tracks location for navigation and mapping.                          |
| **Fingerprint Sensor**  | Provides biometric authentication for security.                      |
| **Heart Rate Sensor**   | Monitors heart rate in fitness or health apps.                       |
| **Microphone**          | Captures sound for voice commands, calls, and recordings.            |

This gives a quick overview of sensor functionality in modern devices!
 **essential code** for each question:

---

### **1. Android Code to Access the Accelerometer and Display X, Y, Z Values**

```java
SensorManager sensorManager = (SensorManager) getSystemService(SENSOR_SERVICE);
Sensor accelerometer = sensorManager.getDefaultSensor(Sensor.TYPE_ACCELEROMETER);

sensorManager.registerListener(new SensorEventListener() {
    @Override
    public void onSensorChanged(SensorEvent event) {
        if (event.sensor.getType() == Sensor.TYPE_ACCELEROMETER) {
            float x = event.values[0];
            float y = event.values[1];
            float z = event.values[2];
            // Display X, Y, Z values
        }
    }

    @Override
    public void onAccuracyChanged(Sensor sensor, int accuracy) {}
}, accelerometer, SensorManager.SENSOR_DELAY_UI);
```

---

### **2. Android Code for Proximity Sensor to Detect Object Proximity**

```java
SensorManager sensorManager = (SensorManager) getSystemService(SENSOR_SERVICE);
Sensor proximitySensor = sensorManager.getDefaultSensor(Sensor.TYPE_PROXIMITY);

sensorManager.registerListener(new SensorEventListener() {
    @Override
    public void onSensorChanged(SensorEvent event) {
        if (event.sensor.getType() == Sensor.TYPE_PROXIMITY) {
            float distance = event.values[0];
            if (distance < proximitySensor.getMaximumRange()) {
                // Object is near
            } else {
                // Object is not near
            }
        }
    }

    @Override
    public void onAccuracyChanged(Sensor sensor, int accuracy) {}
}, proximitySensor, SensorManager.SENSOR_DELAY_UI);
```

---

### **3. Python Code to Read Data from an Accelerometer on a Raspberry Pi**

```python
import time
import board
import busio
import adafruit_adxl34x

i2c = busio.I2C(board.SCL, board.SDA)
accelerometer = adafruit_adxl34x.ADXL345(i2c)

while True:
    x, y, z = accelerometer.acceleration
    print(f"X: {x} m/s^2  Y: {y} m/s^2  Z: {z} m/s^2")
    time.sleep(1)
```

---

These are the most important parts of the code for each case. Let me know if you need any more details!



