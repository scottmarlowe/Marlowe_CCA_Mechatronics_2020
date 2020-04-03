# Marlowe_CCA_Mechatronics_2020

WEEK 1

A simple crank device using pulley and belt to drive a tilting perpendicular lever along a circular cam.

![Crank Device](/Week1/CrankDevice1.jpg)
![Crank Device](/Week1/CrankDevice2.jpg)
![Crank Device](/Week1/CrankDevice3.jpg)

Video
https://youtu.be/jwTeE3iCjKA




WEEK 2

Single crank driving three pulleys with levers and cams. Belts tend to slip and pulleys are being pulled off axis. 
![Crank Device Triple](/Week2/CrankDeviceTriple.gif)




WEEK 3

Motor cannot drive the device due to poor mechanical construction causing wobble and friction.

Failure attempting to drive the belt with separate motor-driven pulley.

![fail1](/Week3/fail1.jpg)

Video
https://youtu.be/JkjAVWVGftY

Failure attempting to directly drive one of the instaled pulleys with motor.

![fail2](/Week3/fail2.jpg)

Video
https://youtu.be/KKH3dOzUtBs

Still works when cranked by hand.

![handdriven](/Week3/handdriven.jpg)

Video
https://youtu.be/ou-ai9QHBVQ




WEEK 4

Playing with LED bulbs

Two alternately blinking lights, I did not get a video of this.
![blinking](/Week4/blinking.jpg)

```CPP
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(8, OUTPUT);
  Serial.begin(9600);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(8, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(1000);// wait for a second
  digitalWrite(8, LOW);
  delay(1000);
  digitalWrite(12, HIGH);    // turn the LED off by making the voltage LOW
  delay(1000);                       // wait for a second
  digitalWrite(12, LOW);
  //send 'Hello, world!' over the serial port
Serial.println("Come on now!");
//wait 100 milliseconds so we don't drive ourselves crazy
delay(1000);
```

A close encounters of the third kind light sequence using delay coding.

![closeencounters](/Week4/closeencounters.jpg)

Video
https://youtu.be/8M5ZBc7ynqw

Light sensor sending information to the computer.

![lightsensors](/Week4/lightsensors.jpg)

Video
https://youtu.be/K-38DAcPvN4




WEEK 5

Considering planetary gears and if they can be used for this project.

![planetarygears](/Week5/planetarygears.jpg)

Video
https://youtu.be/du1b_oT3mYc




WEEK 6

Installed a potentiometer to control an LED.

![potentiometer](/Week6/potentiometer.jpg)

```CPP
// the setup routine runs once when you press reset:
void setup() {
  // initialize serial communication at 9600 bits per second:
  Serial.begin(9600);
  pinMode(A0, INPUT);
}

// the loop routine runs over and over again forever:
void loop() {
  // read the input on analog pin 0:
  int sensorValue = analogRead(A0);
  // print out the value you read:
  Serial.println(sensorValue);
  delay(1);        // delay in between reads for stability

  int outputValue = constrain(sensorValue, 0, 1024);
  outputValue = map(sensorValue, 0, 1024, 255, 0);
  analogWrite(9, outputValue);  
}

```

Installed an ultrasonic sensor to control the brightness of and LED

```CPP
// defines pins numbers
const int trigPin = 9;
const int echoPin = 10;
// defines variables
long duration;
int distance;
int brightness;

void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
Serial.begin(9600); // Starts the serial communication
pinMode(6, OUTPUT);
}
void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);
// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);
// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);
// Calculating the distance
distance= duration*0.034/2;
// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);

//brightness = distance;
distance = constrain(distance, 0, 140);
 brightness = map(distance, 0, 140, 255, 0);
analogWrite(6, brightness);
}

```




WEEK 7

Improved mechanics of the tripple pulley device by installing bearings on pulley axles to dramatically reduce friction.


![bearings](/Week7/bearings.jpg)


![bore](/Week7/bore.jpg)

Satisfying spin Video
https://youtu.be/7d1ex_uC-Dk

Three birds motor driven

![workingmotor](/Week7/workingmotor.jpg)

Video
https://youtu.be/D1ydWNQE_gU

WEEK 8

Three birds rotating at different speeds reletive to eachother with overall speed controlled by single motor connected to an arduino conrolled ultrasonic sensor.

Motor speed controlled by proximity to ultrasonic sensor:

Video
https://youtu.be/zGDzemhVlsw

Images of setup:

New belt heights required a new approach to mounting the motor. Motor with attached pulley installed inversed (motor above pulley) by supporting pulley underneath with additional bearing and building new mount for motor.

![motorcasing](/Week8/motorcasing.jpg)
![motorcasing2](/Week8/motorcasing2.jpg)

Circuitry connecting motor to arduino and supplimentary power source

![circuitry](/Week8/circuitry.jpg)
![curcuitry](/Week8/curcuitry2.jpg)

```CPP

// defines pins numbers
const int trigPin = 9;
const int echoPin = 10;
// defines variables
long duration;
int distance;
int brightness;

void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
Serial.begin(9600); // Starts the serial communication
pinMode(6, OUTPUT);
}
void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);
// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);
// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);
// Calculating the distance
distance= duration*0.034/2;
// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);

//brightness = distance;
distance = constrain(distance, 0, 120);
 brightness = map(distance, 0, 60, 255, 0);
analogWrite(6, brightness);



}
```
![Ultrasonicbirdsfritzing](/Week9/Ultrasonicbirdsfritzing.jpg)
Video:
Final video tour of project and demonstration. Single motor wth pulley driving three additional pullies conected by two belts. Pulley circumferences determine rotational speed in relation to each other (1.5:3:6). Overall speed controlled by proximity to ultrasonic sensor. As one approaches the birds, they begin to fly in circles. the closer you get, the faster they fly.

![Finalvideo](/Week9/Finalvideo.jpg)
https://youtu.be/GVb2Gd1MELI



