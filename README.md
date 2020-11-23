# NotSoBasicArduino
 The follwing files are my second foray into Arduino
 
 
## Table of Contents
* [Table of Contents](#TableOfContents)
* [LED_Fade](#LED_Fade)
* [HelloFunctions](#HelloFunctions)
* [NewPing](#NewPing)
* [Finite LED Blinker](#Finite-LED-Blinker)
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

## HelloFunctions

### Description & Code
Description goes here

Here's how you make code look like code:

```C++
Code goes here
```
Talk about how the code works, here....

### Evidence
link goes here

### Images
draw it yourself, take a picture, make a fritzing, whatever you want to EFFECTIVELY communicate how its put together.

### Reflection

## NewPing

### Description & Code
Description goes here

Here's how you make code look like code:

```C++
Code goes here
```
Talk about how the code works, here....

### Evidence
link goes here

### Images
draw it yourself, take a picture, make a fritzing, whatever you want to EFFECTIVELY communicate how its put together.

### Reflection

