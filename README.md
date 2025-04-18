This project tests the ULN2003A Darlington transistor array using an ESP32/ESP8266 and a simple LED circuit. The setup demonstrates how the ULN2003A sinks current through its outputs when the corresponding input is triggered by a GPIO pin from the ESP. An LED connected between a 5V supply and OUT1 lights up when IN1 is driven HIGH, verifying proper operation of the IC. This test helps in understanding how to interface the ULN2003A with microcontrollers to control loads like LEDs, motors, or relays.

Example code using Arduino IDE-

#include <Stepper.h>

const int stepsPerRevolution = 2048;  // change this to fit the number of steps per revolution

// ULN2003 Motor Driver Pins
#define IN1 19
#define IN2 18
#define IN3 5
#define IN4 17

// initialize the stepper library
Stepper myStepper(stepsPerRevolution, IN1, IN3, IN2, IN4);

void setup() {
  // set the speed at 5 rpm
  myStepper.setSpeed(5);
  // initialize the serial port
  Serial.begin(115200);
}

void loop() {
  // step one revolution in one direction:
  Serial.println("clockwise");
  myStepper.step(stepsPerRevolution);
  delay(1000);

  // step one revolution in the other direction:
  Serial.println("counterclockwise");
  myStepper.step(-stepsPerRevolution);
  delay(1000);
}
