We are very interested in the concept of seeing, the relationship between people who are looking and objects that are being looked at. Somehow, the object could react to the line of sight. It may stares back, feels anxious, turns on, etc, creats tension to attension.

So we hope the installation will 'notice' itself being watched, the more people are gathering, the more excited it will be, the tighter clockspring role and finally hit the soap surface.


![Sensor Test](../project_images/arduino_test1.JPG?raw=true "Sensor Test")
![Sensor Test](../project_images/arduino_test2.JPG?raw=true "Sensor Test")
In terms of device, use infrared sensor switches.



```
const int x1 = 2;//int x to INPUT PIN
const int x2 = 4;
const int x3 = 7;
const int x4 = 8;
const int x5 = 12;
const int x6 = 13;
const int y1 = 3;//int y to OUTPUT PIN
const int y2 = 5;
int a1,a2,a3,a4,a5,a6;
int z = 0;
int b = 0;
#define DIR_PIN 9
#define STEP_PIN 10

void setup()
{
  Serial.begin(57600);
  Serial.println("Start!");  
  pinMode(x1,INPUT);
  pinMode(x2,INPUT);
  pinMode(x3,INPUT);
  pinMode(x4,INPUT);
  pinMode(x5,INPUT);
  pinMode(x6,INPUT);
  pinMode(9, OUTPUT);     
  pinMode(10, OUTPUT);
  digitalWrite(9, LOW);
  digitalWrite(10, LOW);
}

void loop()
{
  int b1 = digitalRead(x1);//first camera
  int b2 = digitalRead(x2);//second camera
  int b3 = digitalRead(x3);//third camera
  int b4 = digitalRead(x4);//forth camera
  int b5 = digitalRead(x5);//fifth camera
  int b6 = digitalRead(x6);//sixth camera
  
   z = b1 + b2 + b3 + b4 + b5 + b;
  if(z == 6){//6 cameras all installed change to 6
    rotate(0,0.5);
  }else {         
    digitalWrite(9, HIGH);
    digitalWrite(10, HIGH);
    delayMicroseconds(400+800*z);
    digitalWrite(10, LOW); 
    delayMicroseconds(400+800*z);
  } 
}

void rotate(int steps, float speed){
  //rotate a specific number of microsteps (8 microsteps per step) - (negitive for reverse movement)
  //speed is any number from .01 -> 1 with 1 being fastest - Slower is stronger
  int dir = (steps > 0)? HIGH:LOW;
  steps = abs(steps);
  digitalWrite(DIR_PIN,dir);
  float usDelay = (1/speed) * 70;
  for(int i=0; i < steps; i++){
    digitalWrite(STEP_PIN, HIGH);
    delayMicroseconds(usDelay);
    digitalWrite(STEP_PIN, LOW);
    delayMicroseconds(usDelay);
  }
}

```

arduino test and it works well.

