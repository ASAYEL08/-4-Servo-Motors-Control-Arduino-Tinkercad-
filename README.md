# 🔌 4-Servo Motors Control (Arduino & Tinkercad)

## 📌 Project Overview
This project demonstrates the control of four servo motors using an Arduino Uno. The operation is divided into two phases: a continuous sweeping motion for a specific duration, followed by a fixed stabilization state.

## 🎯 Objectives
* Implement the standard Servo Sweep pattern across multiple independent motor channels simultaneously.
* Utilize time-based control using millis() to manage operational phases dynamically.
* Command all motors to hold a precise position at 90 degrees upon completing the initial routine.

## 🛠️ Circuit Components & Connections
* 💻 Arduino Uno (Microcontroller)
* ⚙️ 4x Servo Motors
* 🔌 Breadboard for power distribution
* 📍 Pin Mapping:
  * Servo 1 Signal -> Digital Pin 9 (PWM)
  * Servo 2 Signal -> Digital Pin 10 (PWM)
  * Servo 3 Signal -> Digital Pin 11 (PWM)
  * Servo 4 Signal -> Digital Pin 6 (PWM)
  * Power (`VCC` & `GND`) distributed via Breadboard to 5V and GND on Arduino.

## 💻 Code Implementation
```cpp
#include <Servo.h>

Servo servo1;
Servo servo2;
Servo servo3;
Servo servo4;

void setup() {
  servo1.attach(9);
  servo2.attach(10);
  servo3.attach(11);
  servo4.attach(6);
}

void loop() {
  unsigned long startTime = millis();

  while (millis() - startTime < 2000) {
    for (int pos = 0; pos <= 180; pos += 1) {
      servo1.write(pos);
      servo2.write(pos);
      servo3.write(pos);
      servo4.write(pos);
      delay(15);
    }
    for (int pos = 180; pos >= 0; pos -= 1) {
      servo1.write(pos);
      servo2.write(pos);
      servo3.write(pos);
      servo4.write(pos);
      delay(15);
    }
  }

  servo1.write(90);
  servo2.write(90);
  servo3.write(90);
  servo4.write(90);

  while (true) {
  }
}
