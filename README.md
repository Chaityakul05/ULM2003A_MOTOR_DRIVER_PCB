## ULN2003A Test with ESP and Stepper Motor

This project demonstrates how to drive a 28BYJ-48 stepper motor using the ULN2003A Darlington transistor array with an ESP32 or ESP8266. The ULN2003A is used as a current amplifier and switch to control the stepper motor, which requires more current than the ESP GPIO pins can provide directly. The setup connects the ESP to the four input pins (IN1–IN4) of the ULN2003A, which in turn controls the stepper motor connected to the output pins (OUT1–OUT4). This project helps in understanding how to interface stepper motors with microcontrollers through a driver IC and provides basic motion control using the Arduino Stepper library.

---

##  Example Code (Arduino IDE)

```cpp
#include <Stepper.h>

const int stepsPerRevolution = 2048; // Number of steps per full revolution

// ULN2003 Motor Driver Pins
#define IN1 19
#define IN2 18
#define IN3 5
#define IN4 17

// Initialize the stepper library
Stepper myStepper(stepsPerRevolution, IN1, IN3, IN2, IN4);

void setup() {
  // Set the motor speed in RPM
  myStepper.setSpeed(5);
  
  // Start serial communication
  Serial.begin(115200);
}

void loop() {
  // Step one revolution clockwise
  Serial.println("clockwise");
  myStepper.step(stepsPerRevolution);
  delay(1000);

  // Step one revolution counterclockwise
  Serial.println("counterclockwise");
  myStepper.step(-stepsPerRevolution);
  delay(1000);
}

