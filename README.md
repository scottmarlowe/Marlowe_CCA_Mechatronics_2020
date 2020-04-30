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


FINAL PROJECT

Initially, for the final project I was interested in controlling a mechanism through sound frequency and decibles. I was fantisizing about controlling a vehicle by singing to it: higher pitch- turn left, lower pitch- turn right, louder- faster, softer slow. I began by aquiring a sound sensor and began learning how to use it.

Sound Frequency Tutorial:
https://create.arduino.cc/projecthub/calettso/audio-frequency-detector-617856

![frequencydetector](/Finalproject/frequencydetector.jpg)

Code:
I borrowed this code from a gentleman named Clyde Lettsome

```CPP
#include "arduinoFFT.h"
 
#define SAMPLES 128             //SAMPLES-pt FFT. Must be a base 2 number. Max 128 for Arduino Uno.
#define SAMPLING_FREQUENCY 2048 //Ts = Based on Nyquist, must be 2 times the highest expected frequency.
 
arduinoFFT FFT = arduinoFFT();
 
unsigned int samplingPeriod;
unsigned long microSeconds;
 
double vReal[SAMPLES]; //create vector of size SAMPLES to hold real values
double vImag[SAMPLES]; //create vector of size SAMPLES to hold imaginary values
 
void setup() 
{
    Serial.begin(115200); //Baud rate for the Serial Monitor
    samplingPeriod = round(1000000*(1.0/SAMPLING_FREQUENCY)); //Period in microseconds 
}
 
void loop() 
{  
    /*Sample SAMPLES times*/
    for(int i=0; i<SAMPLES; i++)
    {
        microSeconds = micros();    //Returns the number of microseconds since the Arduino board began running the current script. 
     
        vReal[i] = analogRead(0); //Reads the value from analog pin 0 (A0), quantize it and save it as a real term.
        vImag[i] = 0; //Makes imaginary term 0 always

        /*remaining wait time between samples if necessary*/
        while(micros() < (microSeconds + samplingPeriod))
        {
          //do nothing
        }
    }
 
    /*Perform FFT on samples*/
    FFT.Windowing(vReal, SAMPLES, FFT_WIN_TYP_HAMMING, FFT_FORWARD);
    FFT.Compute(vReal, vImag, SAMPLES, FFT_FORWARD);
    FFT.ComplexToMagnitude(vReal, vImag, SAMPLES);

    /*Find peak frequency and print peak*/
    double peak = FFT.MajorPeak(vReal, SAMPLES, SAMPLING_FREQUENCY);
    Serial.println(peak);     //Print out the most dominant frequency.
 
    /*Script stops here. Hardware reset required.*/
    while (1); //do one time
}
```

While the code and the sensor technically worked, I quickly realised that the sensitivity of this particular sensor was going to make it nearly impossible to accurately control the input (it seemed to be detecting sounds and giving back frequencies other than what I was offering). Also, the harmonic nuances of the human voice were going to make it incredibly difficult to identify a particular frequency. At this point I threw in the towel and decided to use what I had been learning about ultrasonic sensors for my final project. We were going to continue making birds fly.

I shifted my vision to creating an apparatus of multiple birds that would be suspend in the air. Using ultrasonic sensors, any birds in the "flock" that a person passed underneath would begin circling above thier head, and would find stillness again as the person left thier vicinity. In an ideal situation with all the time and resources possible, this would be a sprawling installation creating wave patterns of circling birds above people's heads as they passed through the space.

I began by building a simple wooden grid in my garage studio, and suspended a simple motor driven mobile. Using the same proximity/speed code from the previous project I began playing around:

https://youtu.be/Q75GnXtyGvE

I then moved away from proximity and found code that could decelerate the motor after the sensor stopped detecting an object. With Sudhu's help, I tweaked to this:

```CPP
const int trigPin = 6;
const int echoPin = 7;
const int motor = 2;

long duration = 0;
int distance = 0;
int motorSpeed = 0;

void setup() {
  Serial.begin(9600);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(motor, OUTPUT);
}
 
void loop () {
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
Serial.print(distance);
Serial.println(" cm");

analogWrite (motor, motorSpeed);

   if (distance < 60) {  // Distance from sensor
   motorSpeed = 255; // motor ON 
   Serial.print("\t Motor ON");
   Serial.println("\t Motor ON");
}

  else {
    motorSpeed = motorSpeed -1; // motor DECELERATE
    Serial.print("\t Out of range");
    Serial.print("\t Motor OFF");
    Serial.print("\t motorSpeed");
    Serial.println(motorSpeed);
  }

  motorSpeed = constrain(motorSpeed, 0, 255);
 
  delay(50);
```

