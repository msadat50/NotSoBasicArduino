# NotSoBasicArduino
 The follwing files are my second foray into Arduino
 
 
## Table of Contents
* [Table of Contents](#TableOfContents)
* [LED_Fade](#LED_Fade)
* [HelloFunctions](#HelloFunctions)
* [NewPing](#NewPing)
* [Finite LED Blinker](#Finite-LED-Blinker)
* [Variable LED blink and Button Controlled LED](#Variable-LED-blink-and-Button-Controlled-LED)
* [photoresistor](#photoresistor)
---

## LED_Fade

### Description & Code
Description goes here

Here's how you make code look like code:

```C++
  analogWrite(led, brightness);

  // change the brightness for next time through the loop:
  brightness = brightness + fadeAmount;

  // reverse the direction of the fading at the ends of the fade:
  if (brightness <= 0 || brightness >= 255) {
    fadeAmount = -fadeAmount;
  }
```

```C++
void setup() {

  pinMode(13, OUTPUT);      // Set pin 13 to output

}


void loop() {

  digitalWrite(13, HIGH);   // Turn on the LED

  delay(1000);              // Wait for two seconds

  digitalWrite(13, LOW);    // Turn off the LED

  delay(1000);              // Wait for two seconds

}

```
Talk about how the fade works, the fade work really well, the LED turn on and off.

### Evidence
[LED Fade on Arduino Create](https://create.arduino.cc/editor/msadat50/465a684a-ffc7-4daf-b598-ef2f1500eb8a/preview)

### Images
<img src="https://github.com/msadat50/NotSoBasicArduino/blob/main/Images/LED%20Blinked%20.jpg?raw=true" width="400">
<img src="https://github.com/msadat50/NotSoBasicArduino/blob/main/Images/LED%20off.jpg?raw=true"  width="400">

### Reflection
This assignment was really confusing to me, my code was correct but my wiring wasn't correct i join office hours and Mr. H's help me out. one of the wires should be connected in pin 13 in Arduino and in the breadboard it should be in first row, the 2nd wire should be in Arduino GND, and breadboard it should be in row 4. the one leg of resistor should be in row 3 and 4 of breadbored. the LED the short leg should be in row 3 and the long one should be in row 1. 
I leanred how to blink a LED.

## Finite LED Blinker

### Description & Code

```C++
int counter=0; // this is a variable that make the LED blink 5 times
int LED = 13; 

void setup() {
  Serial.begin(9600);
  pinMode(LED, OUTPUT);
}


void loop() {
  if (counter< 5){
  Serial.println(counter);
  digitalWrite(LED, HIGH);   // Turn on the LED
  delay(1000);              // Wait for three seconds
  digitalWrite(LED, LOW);    // Turn off the LED
  delay(1000);              // Wait for three seconds
  counter++; 
  }
}


```
The code workers really well. The LED turns on it wait 3 seconds and than turn off.

### Evidence
[LED Fade on Arduino Create](https://create.arduino.cc/editor/msadat50/b10034a6-c2dd-417c-a08a-d9711166ff4d/preview)

### Images
<img src="https://github.com/msadat50/NotSoBasicArduino/blob/main/Images/LED%20blinking%205%20times.jpg?raw=true"  width="400">
<img src="https://github.com/msadat50/NotSoBasicArduino/blob/main/Images/LED%20close%20wiring%20.jpg?raw=true"  width="400">

### Reflection
This wa our 2nd assignment the wiring is the same thing as the first one. I had trouble doing the code, the only new thing was the (if) and the (count) statement i join officer hours and Mr. H helped me out.

## Variable LED blink and Button Controlled LED

### Description & Code

int ButtonPin = 7;
int LedPin = 13;                   // this is a variable that make the LED blink 5 times
int buttonState = 0;
int delayVar = 1000;      // this variable is used for my delays.

void setup() {
  pinMode(LedPin, OUTPUT);
  pinMode(ButtonPin, INPUT);
  Serial.begin (9600);
  Serial.println("Hello World");
}


void loop() {
  buttonState = digitalRead(ButtonPin);
  Serial.println(buttonState);
  if (buttonState == HIGH) {

    digitalWrite(LedPin, HIGH);   // Turn on the LED
    delay(delayVar);            // wait for a second
    digitalWrite(LedPin, LOW);   // Turn off the LED
    delay(delayVar);          // wait for a second
  }
}

it workd fine
### Evidence
[Variable LED blink and Button Controlled LED on Arduino Create](https://create.arduino.cc/editor/msadat50/820103ac-8c93-4172-900c-dbd65eefa5c6/preview)


### Images
<img src="https://github.com/msadat50/NotSoBasicArduino/blob/main/Images/LED%20button%20off.jpg?raw=true" width="400">
<img src="https://github.com/msadat50/NotSoBasicArduino/blob/main/Images/LED%20button%20on.jpg?raw=true" width="400">

### Reflection
This assignment was really confusing and I had a lot of trouble doing it.The button wire wasn't working. I joined the officer hours Mr.H and Mr.Dierolf helped me figure out the problem, but we could tell what is wrong. so I worked on wiring again by my self when I plug the wire next to LED it was working but when I was plugging the wire next to resistor it wasn't working I don't know why. The next day Mr H came and help me the wiring was wrong. Mr H fixed the wiries the LED is working just fine.


## HelloFunctions

### Description & Code
```C++
#define echoPin 2 // attach pin D2 Arduino to pin Echo of HC-SR04
#define trigPin 3 //attach pin D3 Arduino to pin Trig of HC-SR04
#include <Servo.h>

Servo myServo;
// defines variables
long duration; // variable for the duration of sound wave travel
int distance; // variable for the distance measurement
int cm = 0;
void setup() {
  pinMode(trigPin, OUTPUT); // Sets the trigPin as an OUTPUT
  pinMode(echoPin, INPUT); // Sets the echoPin as an INPUT
  Serial.begin(9600); // // Serial Communication is starting with 9600 of baudrate speed
  Serial.println("Ultrasonic Sensor HC-SR04 Test"); // print some text in Serial Monitor
  Serial.println("with Arduino UNO R3");
  myServo.attach(9);

}
void loop() {
  cm = getDistance();
  // Displays the distance on the Serial Monitor
  Serial.print("Distance: ");
  Serial.print(cm);
  Serial.println(" cm");
  if (cm < 20) {
    myServo.write(90);


  }
  else {
    myServo.write(0);

  }
}






int getDistance() {
  // Clears the trigPin condition
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  // Sets the trigPin HIGH (ACTIVE) for 10 microseconds
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  // Reads the echoPin, returns the sound wave travel time in microseconds
  duration = pulseIn(echoPin, HIGH);
  // Calculating the distance
  distance = duration * 0.034 / 2;   // Speed of sound wave divided by 2 (go and back)
  return distance;

}
```

here is my code it works good. when something or someone is coming near ultrasonic sensor. the servo is turning left, if you're far away than servo turning right.

### Evidence
[Hello Functions on Arudino Create](https://create.arduino.cc/editor/msadat50/c969ac8d-9acf-4491-b26f-4b45bc8ff915/preview)
### Images

<img src="https://github.com/msadat50/NotSoBasicArduino/blob/main/Images/Hello%20funtions.jpg?raw=true" width="400">
<img src="https://github.com/msadat50/NotSoBasicArduino/blob/main/Images/Hello%20funtions%232.jpg?raw=true" width="400">

### Reflection
This is the hello funtion assignment this assignment was good i had trouble coding and wiring it thanks to Mr. H he helped me out.

## NewPing

### Description & Code

```C++
Code #define echoPin 2 // attach pin D2 Arduino to pin Echo of HC-SR04
#define trigPin 3 //attach pin D3 Arduino to pin Trig of HC-SR04
#include <Servo.h>
#include <NewPing.h>
#define MAX_DISTANCE 200
int LedPin = 13;    // this is a variable that make the LED blink 5 times
int delayVar = 1000;  // this variable is used for my delays.


NewPing sonar(trigPin, echoPin, MAX_DISTANCE);


Servo myServo;
// defines variables
long duration; // variable for the duration of sound wave travel
int distance; // variable for the distance measurement
int cm = 0;

void setup() {
  pinMode(13, OUTPUT);  // Set pin 13 to output
  Serial.println("Hello World");
  pinMode(trigPin, OUTPUT); // Sets the trigPin as an OUTPUT
  pinMode(echoPin, INPUT); // Sets the echoPin as an INPUT
  Serial.begin(9600); // // Serial Communication is starting with 9600 of baudrate speed
  Serial.println("Ultrasonic Sensor HC-SR04 Test"); // print some text in Serial Monitor
  Serial.println("with Arduino UNO R3");
  myServo.attach(9);

}
void loop() {
  cm = sonar.ping_cm();     // run the pig cm
  if (cm < 20) {
    digitalWrite(13, HIGH);   // Turn on the LED
    delay(100);              // Wait for two seconds
    digitalWrite(13, LOW);    // Turn off the LED
    delay(100);                    // Wait for two seconds
    myServo.write(90);

  }
  else {
    myServo.write(180);
  }
  Serial.print("Distance: ");
  Serial.print(cm);
  Serial.println(" cm");



} 
```


The code works good. it's a lot similar to hello function assignment just the LED part is different something is colse to ultrasonic sensor the servo turn off and the LED turn on and when something is far away the servo is on and the LED is off.
### Evidence
[New ping  on Arudino Create](https://create.arduino.cc/editor/msadat50/51027bc9-bf28-43cf-aaee-755041d8e175/preview)
[This website helped me with the code](https://create.arduino.cc/projecthub/abdularbi17/ultrasonic-sensor-hc-sr04-with-arduino-tutorial-327ff6)


### Images
<img src="https://github.com/msadat50/NotSoBasicArduino/blob/main/Images/new%20ping.jpg?raw=true" wide="300">
<img src="https://github.com/msadat50/NotSoBasicArduino/blob/main/Images/new%20ping%20led%20on.jpg?raw=true" wide="400">
<img src="https://github.com/msadat50/NotSoBasicArduino/blob/main/Images/new%20ping%20led%20off.jpg?raw=true" wide="400">


### Reflection
This agginment was really confusing ihad trouble wireing and codeing. but Mr. H help me out.
<img src="https://github.com/msadat50/NotSoBasicArduino/blob/main/Images/Screenshot%202020-12-15%20at%204.29.39%20PM.png?raw=true" wide"400">



## photoresistor

### Description & Code
```C++

int lightlevel = 0;
int ledpin = 13;
int photopin = A0;

void setup() {

  pinMode(13, OUTPUT);
  Serial.begin(9600);
  pinMode(photopin, INPUT);

}

void loop() {
  lightlevel = analogRead(photopin);
  Serial.println(lightlevel);
  if (lightlevel < 20) {
    digitalWrite(13, HIGH);   // Turn on the LED
    delay(100);              // Wait for two seconds
    digitalWrite(13, LOW);    // Turn off the LED
    delay(100);                    // Wait for two seconds
  }
  delay(90);

}

```


The code work fine. when a place is dark the LED turn on. when a place is light the LED is off
### Evidence
[ photoresistor on Arudino Create](https://create.arduino.cc/editor/msadat50/2fe9905b-ed36-46f8-88ab-9808c1b40c13/preview)

### Images
<img src="https://github.com/msadat50/NotSoBasicArduino/blob/main/Images/Photoresistor%20led%20on.jpg?raw=true" wide="400">
<img src="https://github.com/msadat50/NotSoBasicArduino/blob/main/Images/Photoresistor%20led%20off.jpg?raw=true" wide="400">

### Reflection
This assignment was easier than the two other assignments.I kind off had trouble doing the code thanks to Mr. Dierolf he helped me out. i didn't had any trouble doing the wiring. 
