Code for IMU Sensor
#include "Arduino_BMI270_BMM150.h"

float x, y, z;
int degreesX = 0;
int degreesY = 0;

void setup() {
  Serial.begin(9600);
  while (!Serial);
  Serial.println("Started");
  if (!IMU.begin()) {
    Serial.println("Failed to initialize IMU!");
    while (1);
  }
  Serial.print("Accelerometer sample rate = ");
Serial.print(IMU.accelerationSampleRate());
  Serial.println(" Hz");
}

void loop() {
  float x, y, z;
  if (IMU.accelerationAvailable()) {
    IMU.readAcceleration(x, y, z);
if(x > 0.1){
    x = 100*x;
    degreesX = map(x, 0, 97, 0, 90);
    Serial.print("Tilting up ");
    Serial.print(degreesX);
    Serial.println("  degrees");
    }
  if(x < -0.1){
    x = 100*x;
    degreesX = map(x, 0, -100, 0, 90);
    Serial.print("Tilting down ");
    Serial.print(degreesX);
    Serial.println("  degrees");
    }
  if(y > 0.1){
    y = 100*y;
    degreesY = map(y, 0, 97, 0, 90);
    Serial.print("Tilting left ");
    Serial.print(degreesY);
    Serial.println("  degrees");
    }
  if(y < -0.1){
    y = 100*y;
    degreesY = map(y, 0, -100, 0, 90);
    Serial.print("Tilting right ");
    Serial.print(degreesY);
    Serial.println("  degrees");
    }
  }
}

}

Code for Temperature and Humidity sensor 
#include <Arduino_HS300x.h>
float old_temp = 0;
float old_hum = 0;

void setup() {
  Serial.begin(9600);
  while (!Serial);
  if (!HS300x.begin()) {
    Serial.println("Failed to initialize humidity temperature sensor!");
    while (1);
  }
}

void loop() {
  float temperature = HS300x.readTemperature();
  float humidity = HS300x.readHumidity();
  if (abs(old_temp - temperature) >= 0.5 || abs(old_hum - humidity) >= 1) {
    Serial.print("Temperature = ");
    Serial.print(temperature);
    Serial.println("°C");
    Serial.print("Humidity = ");
    Serial.print(humidity);
    Serial.println("%");
    Serial.println();
    delay(1000);
  }
}


