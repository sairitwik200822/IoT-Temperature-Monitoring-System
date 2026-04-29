# IoT Temperature Monitoring System

##  Overview
This project monitors temperature using a sensor and displays the data using Arduino. It can be extended for IoT-based remote monitoring.

## Components Used
- Arduino Uno
- Temperature Sensor (DS18B20 / DHT22)
- Jumper Wires

##  Working Principle
The temperature sensor reads environmental temperature and sends data to the Arduino. The Arduino processes the data and displays it via Serial Monitor.

## Code Features
- Sensor data reading
- Real-time monitoring
- Serial output display

##  Future Improvements
- WiFi-based monitoring (ESP8266)
- Mobile app integration
- Data logging
- triggering an alarm or buzzer when temperature reaches a certain threshold

## CODE

#include <DHT.h>

#define DHTPIN 2        // Data pin connected to Arduino

#define DHTTYPE DHT22   // Change to DHT11 if needed

DHT dht(DHTPIN, DHTTYPE);

void setup() 

{

  Serial.begin(9600);
  
  dht.begin();
  
  Serial.println("Temperature 
  
  Monitoring System Started...");
  
}

void loop() 
{

  float temperature = 
  
  dht.readTemperature();
  
  float humidity = dht.readHumidity();

  if (isnan(temperature) || 
  
  isnan(humidity)) 
  {
  
    Serial.println("Failed to read from DHT sensor!");
    
    return;
    
  }

  Serial.print("Temperature: ");
  
  Serial.print(temperature);
  
  Serial.print(" °C  |  Humidity: ");
  
  Serial.print(humidity);
  
  Serial.println(" %");

  delay(2000); // Read every 2 seconds
  
}
