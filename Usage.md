Upload the Code to Your Arduino
After setting up your IDE and installing the required libraries (see Installation Instructions), follow these steps:

Open the .ino file (e.g., HS300x_TempHum.ino) in Arduino IDE.

Ensure these settings under the Tools menu:

Board: Arduino Nano 33 BLE Sense

Port: [Your connected USB port]

Click Upload to flash the code onto your board.

View Output via Serial Monitor
Once the code is uploaded:

Go to Tools > Serial Monitor or press Ctrl + Shift + M.

Set the baud rate to 9600.

You should see output like:

Temperature = 25.2°C
Humidity = 49%


If the sensor fails to initialize, you’ll see:
Failed to initialize humidity temperature sensor!

How the Code Works
It only prints new values if there's a significant change:

Temperature change ≥ 0.5°C

Humidity change ≥ 1%

This avoids cluttering the output with redundant data.
Modifying the Code
You can customize the behavior easily:
Change reporting thresholds:

if (abs(old_temp - temperature) >= 0.5 || abs(old_hum - humidity) >= 1)
→ You can adjust 0.5 and 1 to finer or coarser thresholds.

Adjust the delay between readings:

delay(1000);  // delay in milliseconds (1000 ms = 1 second)
You can add more Serial.print() lines if you want extra formatting or logging.

Using Serial Plotter
Go to Tools > Serial Plotter

You’ll be able to visualize temperature and humidity changes over time.

Make sure your print lines match a key = value format, like:
Serial.print("Temperature=");
Serial.println(temperature);
