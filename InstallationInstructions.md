# Arduino Nano 33 BLE Sense – IMU and Temperature Sensor

This project demonstrates how to interface with onboard sensors on the **Arduino Nano 33 BLE Sense Rev2**, specifically the **BMI270_BMM150 IMU** and the **HS300x temperature and humidity sensor**. The goal is to read real-time environmental and motion data using C++ and the Arduino IDE.

## 🔧 Installation Instructions

Follow these steps to set up your development environment:

1. Install Arduino IDE 
   Download it from [arduino.cc](https://www.arduino.cc/en/software).

2. Add the Board Package  
   - Go to Tools > Board > Boards Manager
   - Search for and install:  
     "Arduino Mbed OS Nano Boards" 
     (includes Nano 33 BLE Sense)

3. Connect Your Board  
   - Plug in the Arduino Nano 33 BLE Sense Rev2 via USB
   - Select the correct "board" and "port" from the "Tools" menu

4. Install Required Libraries 
   - Open Library Manager (`Sketch > Include Library > Manage Libraries`)
   - Install:
     - `Arduino_HS300x`
     - `Arduino_BMI270_BMM150`

5. Clone This Repository
   ```bash
   git clone https://github.com/ritikaalla06/Advance_Programing-.git
