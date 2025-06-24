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
