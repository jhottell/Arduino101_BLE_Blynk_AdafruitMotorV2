/**************************************************************
 * This sketch is for an Arduino 101 BLE rover using Blynk and Adafruit Motor Shield V2
 * Code was copied from both Adafruit and Blynk librarie examples
 * Full documentation on building this rover yourself on Hackster.IO and electronhacks.com
 * Sketch is released under MIT license
 **************************************************************/


#define BLYNK_PRINT Serial
#include <BlynkSimpleCurieBLE.h>
#include <CurieBLE.h>
#include <Wire.h>
#include <Adafruit_MotorShield.h>
#include "utility/Adafruit_MS_PWMServoDriver.h"

// You should get Auth Token in the Blynk App.
// Go to the Project Settings (nut icon).
char auth[] = "1b393b0f3f4f4245ba98929f225fa9cb";

BLEPeripheral  blePeripheral;

// Create the motor shield object with the default I2C address
Adafruit_MotorShield AFMS = Adafruit_MotorShield(); 

// Select which 'port' M1, M2, M3 or M4.
Adafruit_DCMotor *motor1 = AFMS.getMotor(1);
Adafruit_DCMotor *motor2 = AFMS.getMotor(2);


//######### SETUP ######################################
void setup() {
  Serial.begin(9600);
  delay(1000);

  // The name your bluetooth service will show up as, customize this if you have multiple devices
  blePeripheral.setLocalName("Arduino101Blynk");
  blePeripheral.setDeviceName("Arduino101Blynk");
  blePeripheral.setAppearance(384);

  Blynk.begin(auth, blePeripheral);

  blePeripheral.begin();
  Serial.println("Waiting for connections...");
    
  Serial.println("Adafruit Motorshield v2 - DC Motor");

  AFMS.begin();  // create with the default frequency 1.6KHz
  //AFMS.begin(1000);  // OR with a different frequency, say 1KHz
  
  // Set the speed to start, from 0 (off) to 255 (max speed)
  motor1->setSpeed(255);
  motor2->setSpeed(255);
  

}


//########## LOOP ######################################
void loop() {
  Blynk.run();
  blePeripheral.poll();
}


//######### Subrutines ################################

// This function will set the speed
BLYNK_WRITE(V0)
{
  int pinValue = param.asInt(); // assigning incoming value from pin V1 to a variable
  // You can also use:
  // String i = param.asStr();
  // double d = param.asDouble();
  Serial.print("V0 Slider value is: ");
  Serial.println(pinValue);
  motor1->setSpeed(pinValue);
  motor2->setSpeed(pinValue); 
}

// Motor 1 Forward
BLYNK_WRITE(V1)
{
  int pinValue = param.asInt(); // assigning incoming value from pin V1 to a variable
  Serial.print("Motor 1 Forward: ");
  Serial.println(pinValue);
  if(pinValue == 1) {
    motor1->run(FORWARD);
  }
  if(pinValue == 0) {
    motor1->run(RELEASE);
  }
}


// Motor 2 Forward
BLYNK_WRITE(V2)
{
  int pinValue = param.asInt(); // assigning incoming value from pin V1 to a variable
  Serial.print("Motor 2 Forward: ");
  Serial.println(pinValue);
  if(pinValue == 1) {
    motor2->run(FORWARD);
  }
  if(pinValue == 0) {
    motor2->run(RELEASE);
  }
}

// Motor 1 Backward
BLYNK_WRITE(V3)
{
  int pinValue = param.asInt(); // assigning incoming value from pin V1 to a variable
  Serial.print("Motor 1 Backward: ");
  Serial.println(pinValue);
  if(pinValue == 1) {
    motor1->run(BACKWARD);
  }
  if(pinValue == 0) {
    motor1->run(RELEASE);
  }
}

// Motor 2 Backward
BLYNK_WRITE(V4)
{
  int pinValue = param.asInt(); // assigning incoming value from pin V1 to a variable
  Serial.print("Motor 2 Backward: ");
  Serial.println(pinValue);
  if(pinValue == 1) {
    motor2->run(BACKWARD);
  }
  if(pinValue == 0) {
    motor2->run(RELEASE);
  }
}
