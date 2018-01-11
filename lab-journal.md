# Lab Journal, ROCO222 By Alex Dooley

<img src="https://github.com/ajdooley/lab-journal/blob/master/20170925_100923.jpg" width="700" height="400" />

# Practical 1:

## Markdown:  
A lightweight markup language with a plain text formatting syntax. Designed so that conversion to HTML is possible and other formats using a tool. 

## Key Rules: 
Two underscores/* means that the enclosed text becomes bold. 
One underscore/* means that the enclosed text becomes italic. 
Two ~ means that the text has a strikethrough. 
Lists can be made by typing numbers followed by a dot and a space. 
Three spaces can be used to indent a paragraph. 
[Anchor Text](Link "Title") 
# = H1, ## = H2 etc. 
Reference Style Image: ![alt text] [logo] [logo]: link "title" 
`Inline Code` 
 > Creates a block quote 
Three of more ---, ***, ___ creates a solid horizontal line. 

Use git init to create a Git Repository 
Permissions / User / Bits / Creation date 

## Hack Into A Robot: 

The robot was networked and we were given an IP address. 
IP: 192.168.0.184

Some of the code used to make the robot speak was the following:

```
tts = ALProxy("ALTextToSpeech", "localhost", 9559)
tts.say("I've hacked you, robot!")
```

# Practical 2: 
## DC Motor: 

This task consisted of constructing a very basic DC motor. 

<img src="https://github.com/ajdooley/lab-journal/blob/master/Untitled-7.fw.png" width="550" height="450" />

## In Motion: 

<img src="https://github.com/ajdooley/lab-journal/blob/master/Untitled-6.fw.png" width="600" height="400" />

## Basic Motor Design: 

We created a simple yet effective DC motor using a cork as a commutator and armature in one. 

<img src="https://github.com/ajdooley/lab-journal/blob/master/Untitled-5.fw.png" width="700" height="500" />

## Taking It Further: 

Having produced a working DC motor using a single coil, we decided to try and produce one using 4 coils. We 3D printed mounting and attached it to a larger piece of plywood. In order to make this motor turn faster, we used thicker gauge copper wire in order to take a higher current and more windings. We also stacked up far more magnets. 

In order to produce this new motor we used the following:

* 1x 300mm of 8mm threadded rod
* 2x 608Z bearings
* 50x 8mm washers
* 50x 8mm nuts
* 500g Thinly insulated copper wire
* Many cups of coffee
* PETG Filament for 3D Printing

## 3D printing: 

<img src="https://github.com/ajdooley/lab-journal/blob/master/Untitled-4.fw.png" width="450" height="500" />

## Commutator construction: 

Using two pieces of copper tape and a 3D printed commutator, we produced a fairly efficient commutator. 

## Armature winding: 

We used far more turns in the copper wire this time, and made sure the windings were tightly wound. 


# Practical 3:  
## Incremental Encoder: 

<img src="https://github.com/ajdooley/lab-journal/blob/master/Untitled-3.fw.png" width="650" height="500" />

## 3D Printing And Mounting: 

We 3D printed a disk with a slot in it. This would attach to the motor shaft and spin. An LED light source and phototransistor detector would then detect each rotation as a signal is picked up when the slot is between the LED and detector. 

<img src="https://github.com/ajdooley/lab-journal/blob/master/Untitled-2.fw.png" width="500" height="500" />

## The Circuit:  

<img src="https://github.com/ajdooley/lab-journal/blob/master/20180110_152903.jpg" width="550" height="300" />

# Practical 4:  
## Controlling The Motor: 

We connected the motor we had build to the motor shield in order to control the speed.

## Motor Shield: 

<img src="https://github.com/ajdooley/lab-journal/blob/master/20180110_154243.jpg" width="700" height="400" />

## Coding: 

```
const byte interruptPin = 2;

volatile byte state = LOW;

unsigned long count = 0;

boolean counted = false;


void setup() 

{

  Serial.begin(9600);
  
  pinMode(interruptPin, INPUT);
  
  //attachInterrupt(digitalPinToInterrupt(interruptPin), blinkup, RISING);
  
  attachInterrupt(digitalPinToInterrupt(interruptPin), blinkdown, CHANGE);
  
}

void loop() {

  delay(1000);
  
  count = count*60/4/6.3;
  
  Serial.println(count);
  
  count = 0;
  
}

*/

void blinkup() 

{

  if (counted == false)
  
  {
  
    counted = true;
    
  }
  
}

*/

void blinkdown() 

{

  //if (counted == true){
  
    count ++;
    
    //counted = false;
    
  }
  
}
```


# Practical 5:  
## Stepper motors And Arduino : 

<img src="https://github.com/ajdooley/lab-journal/blob/master/Stepper.jpg" width="600" height="350" />

## Wiring Up A Stepper Motor: 

<img src="https://github.com/ajdooley/lab-journal/blob/master/Connecting.jpg" width="500" height="350" />

## Bipolar Vs Unipolar Stepper Motor: 

<img src="https://github.com/ajdooley/lab-journal/blob/master/Polar.gif" width="650" height="400" />

Image taken from: https://www.circuitspecialists.com/blog/unipolar-stepper-motor-vs-bipolar-stepper-motors/

-------------------------------- 
# Robotic Arm Project: 

<img src="https://github.com/ajdooley/lab-journal/blob/master/20180110_182458.jpg" width="600" height="350" />

Testing the servos:

<img src="https://github.com/ajdooley/lab-journal/blob/master/20171106_103548.jpg" width="650" height="350" />
 
<img src="https://github.com/ajdooley/lab-journal/blob/master/20171127_093756.jpg" width="650" height="350" />

## Wiring The Servos: 

<img src="https://github.com/ajdooley/lab-journal/blob/master/20180110_154528.jpg" width="700" height="400" />

## Controlling A Servo: 

<img src="https://github.com/ajdooley/lab-journal/blob/master/20171106_103553.jpg" width="650" height="350" />
 

## Using ROS: 

```
#include <Servo.h>

Servo myservo;

int pos = 0;


void setup() {

  myservo.attach(9); // attaches the servo on pin 9 to the servo object

}

void loop() {

  for (pos = 0; pos <= 180; pos += 1) {

    // in steps of 1 degree

    myservo.write(pos);

    delay(15);

  }

  for (pos = 180; pos >= 0; pos -= 1) {

    myservo.write(pos);

    delay(15);

  }

}
```

<img src="https://github.com/ajdooley/lab-journal/blob/master/20180110_182504.jpg" width="650" height="350" />

<img src="https://github.com/ajdooley/lab-journal/blob/master/20180110_182511.jpg" width="650" height="350" />

## URDF Model: 



## Visualized 3D Model: 

 

## Move It: 
http://docs.ros.org/kinetic/api/moveit_tutorials/html/index.html 
