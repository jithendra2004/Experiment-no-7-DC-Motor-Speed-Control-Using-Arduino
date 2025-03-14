# Experiment-no-7-DC-Motor-Speed-Control-Using-Arduino

### AIM : 
To control the speed and the direction of a DC motor using L293D driver ic( H- bridge)

### Components Required:
    •	Arduino UNO board
    •	L293D driver
    •	12V DC motor
    •	10K ohm potentiometer
    •	Pushbutton
    •	12V source
    •	Breadboard
    •	Jumper wires
### THEORY 
The L293D quadruple half-H drivers chip allows us to drive 2 motors in both directions, with two PWM outputs from the Arduino we can easily control the speed as well as the direction of rotation of one DC motor. (PWM: Pulse Width Modulation).

Arduino DC motor control circuit:

Project circuit schematic diagram is the one below.

![image](https://user-images.githubusercontent.com/36288975/167763051-b230c183-afc5-46f2-ba95-0f95e10dd6c9.png)
FIGURE-01 H BRIDGE CIRUCIT INTERFACE 
 
The speed of the DC motor (both directions) is controlled with the 10k potentiometer which is connected to analog channel 0 (A0) and the direction of rotation is controlled with the push button which is connected to pin 8 of the Arduino UNO board. If the button is pressed the motor will change its direction directly.
The L293D driver has 2 VCCs: VCC1 is +5V and VCC2 is +12V (same as motor nominal voltage). Pins IN1 and IN2 are the control pins where:
![image](https://user-images.githubusercontent.com/36288975/167763120-1421c2c5-8381-49eb-b376-03f6e1113b7a.png)

TABLE-01 EXITATION TABLE FOR H BRIDGE 

As shown in the circuit diagram we need only 3 Arduino terminal pins, pin 8 is for the push button which toggles the motor direction of rotation. Pins 9 and 10 are PWM signal outputs, at any time there is only 1 active PWM, this allows us to control the direction as well as the speed by varying the duty cycle of the PWM signal. The active PWM pin decides the motor direction of rotation (one at a time, the other output is logic 0).

### PRGORAM 
```
NAME:V.A.JITHENDRA
REG.NO:212221230043

```
### Normal RPM:
```
const int motorpin1 = 5;
const int motorpin2 = 6;

void setup()
{
  pinMode(motorpin1, OUTPUT);
  pinMode(motorpin2, OUTPUT);
}

void loop()
{
  digitalWrite(motorpin1, HIGH);
  delay(2000);
  digitalWrite(motorpin2, LOW);
  delay(2000);
}
```
### To Control RPM:
```
#define motorIn1 5
#define motorIn2 6

void setup()
{
  pinMode(motorIn1,OUTPUT);
  pinMode(motorIn2,OUTPUT);
}
void loop()
{
  clockwise(0);
  delay(3000);
  counterclockwise(50);
  delay(3000);
}
void counterclockwise(int speed)
{
  analogWrite(motorIn1,speed);
  analogWrite(motorIn2,0);
}

void clockwise(int speed)
{
  
  analogWrite(motorIn1,0);
  analogWrite(motorIn2,speed);
}
```
### OUTPUT
### CIRCUIT

![1](https://user-images.githubusercontent.com/94226297/198178457-7bb8d1a3-8c65-47ff-a570-80c4e6437d5e.png)
 DIAGRAM:

### READINGS:
### CLOCKWISE:
![s1](https://user-images.githubusercontent.com/94226297/198178505-c73e8343-7da2-406c-9226-4bbf63148ed4.png)


#### GRAPH:
![2](https://user-images.githubusercontent.com/94226297/198178533-1435f643-d4b1-48ca-8283-a3a2d2c34eee.png)


### COUNTER CLOCKWISE:
![s2](https://user-images.githubusercontent.com/94226297/198178573-b68698f2-339c-4c45-90d4-b3edf203ad99.png)

#### GRAPH:
![3](https://user-images.githubusercontent.com/94226297/198178620-06561add-6c48-4d55-98e1-d7b2830742e9.png)


### RESULT :

Thus, the speed and the direction of a DC motor using L293D driver ic( H- bridge) is controlled.
