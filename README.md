# Digital Thermometer using Arduino and LCD 🌡️  

## Overview  
This project is a simple digital thermometer using an Arduino and an LCD display to measure and show the temperature in Fahrenheit.

## Components Used  
- Arduino UNO  
- 16x2 LCD Display  
- Temperature Sensor  
- Jumper Wires  

## How It Works  
- Reads temperature from a sensor.
- Converts the analog sensor value into a readable temperature.
- Displays the temperature on the LCD in Fahrenheit.

## Code  
```cpp
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
int degree;
double realdegree;

void setup() {
  lcd.begin(16, 2);
  degree = 0;
  realdegree = 0.0;
  lcd.print("Today's Temp:");
}

void loop() {
  degree = analogRead(0);
  
  realdegree = (double)degree / 1024;
  realdegree *= 5;
  realdegree -= 0.5;
  realdegree *= 100;
  
  lcd.setCursor(0, 1);
  realdegree = (9.0 / 5) * (realdegree) + 32;
  String output = String(realdegree) + String((char)178) + "F";
  lcd.print(output);
}
