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

During my early explorations of a mobile apparatus using wooden disks suspended on strings, I realized that the inertia of the motor starting up caused the strings to immediately tangle. So, I moved them all to one side of the motor wheel to create a circling flock effect. Then, an obvious problem. With the ultrasonic sensor positioned to project downward near the mobile, once the motor started running, the sensor would detect the passing objects and constantly rev back up to full power, never decelerating. I had created a never ending cycle.

https://youtu.be/plBLBUfeJcc

The next challenge was to get multiple sensors communicating through one Arduino. Again, I went in search of existing code as a foundation for what I wanted to achieve. I found code for five sensors and expanded it to include a sixth.

![sixsensors](/Finalproject/sixsensors.jpg)

Two of the sensors were not responding, a third would only register a distance of zero, so I ripped out those three sensors and moved forward (this was a blessing in disguise, later I realized my studio space would have been too small to accomodate six of these apparatus.

Code for three sensors. Original code by Robomechtrix:
```CPP
//int trigPin1=2;
//int echoPin1=3;

//int trigPin2=4;
//int echoPin2=5;

int trigPin3=6;
int echoPin3=7;
int motor3=2;

//int trigPin4=8;
//int echoPin4=9;

int trigPin5=10;
int echoPin5=11;
int motor5=3;

int trigPin6=12;
int echoPin6=13;
int motor6=4;

void setup() {
  Serial.begin (9600);
  //pinMode(trigPin1, OUTPUT);
  //pinMode(echoPin1, INPUT);
  //pinMode(trigPin2, OUTPUT);
  //pinMode(echoPin2, INPUT);
  pinMode(trigPin3, OUTPUT);
  pinMode(echoPin3, INPUT);
  //pinMode(trigPin4, OUTPUT);
  //pinMode(echoPin4, INPUT);
  pinMode(trigPin5, OUTPUT);
  pinMode(echoPin5, INPUT);
  pinMode(trigPin6, OUTPUT);
  pinMode(echoPin6, INPUT);

}

  void loop() {
  long duration3, distance3;
  digitalWrite(trigPin3, LOW); 
  delayMicroseconds(2); 
  digitalWrite(trigPin3, HIGH);
  delayMicroseconds(10); 
  digitalWrite(trigPin3, LOW);
  duration3 = pulseIn(echoPin3, HIGH);
  distance3= (duration3/2) / 29.1;

   if (distance3 >= 100 || distance3 <= 0){
    Serial.println("Out of range");
  }
  else {
    Serial.print("Sensor3  ");
    Serial.print(distance3);
    Serial.println("cm");
  }
 

   delay(10);
     long duration5, distance5;
  digitalWrite(trigPin5, LOW); 
  delayMicroseconds(2); 
  digitalWrite(trigPin5, HIGH);
  delayMicroseconds(10); 
  digitalWrite(trigPin5, LOW);
  duration5 = pulseIn(echoPin5, HIGH);
  distance5 = (duration5/2) / 29.1;

   if (distance5 >= 100 || distance5 <= 0){
    Serial.println("Out of range");
  }
  else {
    Serial.print ( "Sensor5  ");
    Serial.print ( distance5);
    Serial.println("cm");
  }

   delay(10);
     long duration6, distance6;
  digitalWrite(trigPin6, LOW); 
  delayMicroseconds(2); 
  digitalWrite(trigPin6, HIGH);
  delayMicroseconds(10); 
  digitalWrite(trigPin6, LOW);
  duration6 = pulseIn(echoPin6, HIGH);
  distance6 = (duration6/2) / 29.1;

   if (distance6 >= 100 || distance6 <= 0){
    Serial.println("Out of range");
  }
  else {
    Serial.print ( "Sensor6  ");
    Serial.print ( distance6);
    Serial.println("cm");
  }

   delay(10);
  }
  ```
Now, I needed to figure out how to use these three sensors to conrol three separate motors.

![3sensors3motors](/Finalproject/3sensors3motors.jpg)

Again, with Sudhu's assistance, I integrated our "deceleration code" into the code for three ultrasonic sensors. When the motors were not properly decelerating, he pointed out that I was using a digital input pin rather than an analogue pin. Thank you! Finally the thing was working, kind of. Two of the motors were still not responding as intended. They would not engage until AFTER they stopped detecting an object. I investigated, did some research, and discovered several brackets and semi-colons that needed to be moved or deleted. Success.

https://youtu.be/OC8mFgH-Kdw


```CPP
const int trigPin1 = 7;
const int echoPin1 = 8;
const int motor1 = 5;
int motor1Speed = 0;


const int trigPin2 = 12;
const int echoPin2 = 13;
const int motor2 = 3;
int motor2Speed = 0;

const int trigPin3 = 2;
const int echoPin3 = 4;
const int motor3 = 9;
int motor3Speed = 0;



void setup() {
  Serial.begin (9600);
  pinMode(trigPin1, OUTPUT);
  pinMode(echoPin1, INPUT);
  pinMode(trigPin2, OUTPUT);
  pinMode(echoPin2, INPUT);
  pinMode(trigPin3, OUTPUT);
  pinMode(echoPin3, INPUT);

}

void loop() {
  // Sensor 1 ==================================================================
  long duration1, distance1;
  digitalWrite(trigPin1, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin1, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin1, LOW);
  duration1 = pulseIn(echoPin1, HIGH);
  distance1 = (duration1 / 2) / 29.1;

  if (distance1 <= 60) {  // Distance from sensor
    motor1Speed = 255; // motor ON
    Serial.print("\t Motor1 ON");
  }  else {
    motor1Speed = motor1Speed - 5; // motor DECELERATE
    Serial.print("\t Decelerate");
  }

  motor1Speed = constrain(motor1Speed, 0, 255);
  analogWrite(motor1, motor1Speed);
  Serial.print("\t motor1Speed");
  Serial.println(motor1Speed);

// =========================================================
// Sensor 1 END =====================================================
// =========================================================


delay(50);

// Sensor 2 =================================================================

long duration2, distance2;
digitalWrite(trigPin2, LOW);
delayMicroseconds(2);
digitalWrite(trigPin2, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin2, LOW);
duration2 = pulseIn(echoPin2, HIGH);
distance2 = (duration2 / 2) / 29.1;

if (distance2 <= 60) {  // Distance from sensor
  motor2Speed = 255; // motor ON
  Serial.print("\t Motor2 ON");
}  else {
  motor2Speed = motor2Speed - 5; // motor DECELERATE
  Serial.print("\t Decelerate");
}
  motor2Speed = constrain(motor2Speed, 0, 255);
  analogWrite(motor2, motor2Speed);
  Serial.print("\t motor2Speed");
  Serial.println(motor2Speed);

// ====================================
// Sensor 2 END ======================================
// ====================================

delay(50);

// Sensor 3 ======================================================================
long duration3, distance3;
digitalWrite(trigPin3, LOW);
delayMicroseconds(2);
digitalWrite(trigPin3, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin3, LOW);
duration3 = pulseIn(echoPin3, HIGH);
distance3 = (duration3 / 2) / 29.1;

if (distance3 <= 60) {  // Distance from sensor
  motor3Speed = 255; // motor ON
  Serial.print("\t Motor3 ON");
}  else {
  motor3Speed = motor3Speed - 5; // motor DECELERATE
  Serial.print("\t Decelerate");

}
  motor3Speed = constrain(motor3Speed, 0, 255);
  analogWrite(motor3, motor3Speed);
  Serial.print("\t motor3Speed");
  Serial.println(motor3Speed);


delay(50);
}
// ====================================
// Sensor 3 END ======================================
// ====================================
```

Then it was time to install. Before unhooking the motors and sensors from the board I meticulously labeled all the conections so as to avoid any frustrating guesswork or confusion later.

I mounted the three sensors to hang from the grid on the periphery of the space to avoid any mobiles from self triggering (in a larger space with many more apparatus a different solution would need to be designed).

![sensorspremount](/Finalproject/sensorspremount.jpg)
![sensorsmounted](/Finalproject/sensorsmounted.jpg)

The arduino, breadbord, and power supplies are mounted at the ceter of the grid.

![boardmount](/Finalproject/boardmount.jpg)

20 gauge "bell wire" is used to connect all the sensors and motors to the board.

![bellwire](/Finalproject/bellwire.jpg)
![gridwires](/Finalproject/gridwires.jpg)

The stage is set.

![stageset](/Finalproject/stageset.jpg)

And the system works. As long as you remain in proximity to any particular mobile apparatus, the bird(s) will fly at full speed. The moment you move away, the birds glide to a stop.

Bird installation in action:

https://youtu.be/otABHn40RxY


