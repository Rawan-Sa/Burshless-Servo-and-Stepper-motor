#Brusless-motor
# Tinkercad was used to write the code and design the Brushless motor circuit.
# arduino Uno R3, DC motor, Potentiometer and H-bridge motor drive were mainly used to make the circuit.
# i used DC motor instead of brushless motor because Tinkercad does not offer any.

int potIn;
int fwdPin = 5;
int revPin = 6;

void setup()
{
  
  pinMode(fwdPin , OUTPUT);
  
  pinMode(revPin , OUTPUT);
  
Serial.begin(9600);  
  
}

void loop()
{
  
 potIn = analogRead(A0);
  
  int output = potIn/4;
  
  analogWrite(revPin , output);
  
  delay(100);
  
}

# Stepper-motor
# Tinkercad was used to write the code and design the Stepper motor circuit.
# arduino Uno R3 and DC motor with encoder was the main parts to make the Stepper motor circuit.

#include <Stepper.h>:

const int stepsPerRevolution = 120;

Stepper myStepper (stepsPerRevolution , 1 , 9 , 10 , 11);

int stepCount = 0;

void setup() {
Serial.begin(9600);

}

void loop() {
  int sensorReading = analogRead(A0);
  int motorSpeed = map(sensorReading , 0 , 1023 , 0 , 250); 
  if (motorSpeed > 0 ){
   myStepper.setSpeed(motorSpeed);
    myStepper.step(stepsPerRevolution / 100);
    
  }
}

# Servo-motor
# using Tinkercad to design and code the Servo motor circuit

#include <Servo.h>
Servo servo1;
int pos =0;
void setup()
{
  servo1.attach(13);// because signal pin is connected with 13
}

void loop()
{
  // rotate from 0 to 180 degree
  for(pos=0;pos<=180;pos++){
    servo1.write(pos);
    delay(15);}
  for(pos=10;pos>=0;pos--){
    servo1.write(pos);
    delay(15);}
    
}
