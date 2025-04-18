## ULN2003A Test with ESP and Stepper Motor

This project tests the ULN2003A Darlington transistor array using an ESP32/ESP8266 and a simple LED circuit. The setup demonstrates how the ULN2003A sinks current through its outputs when the corresponding input is triggered by a GPIO pin from the ESP. An LED connected between a 5V supply and OUT1 lights up when IN1 is driven HIGH, verifying proper operation of the IC. This test helps in understanding how to interface the ULN2003A with microcontrollers to control loads like LEDs, motors, or relays.

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

