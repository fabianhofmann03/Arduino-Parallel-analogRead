# Arduino-Parallel-analogRead
An Arduino library for non-blocking analogRead.

I'm not familiar with the ADC of the Arduino-Microcontroller, so most of the code is copied. I'm not sure what source I had when I made it, but I'm pretty sure it was this one: https://www.arduinoslovakia.eu/blog/2018/9/a/d-prevodnik---meranie-bez-blokovania?lang=en

## Working on
- Arduino Uno (I think)

Please try yourself if the library is working on your Arduino.

## How to use
### setup()
Set up the ADC.
### startMeasurement(int pin)
Start the measurement on the pin given as parameter.
### resultAvailable()
Returns `true` if the result is available. If not it returns `false`.
### resultWasRead()
Returns `true` if the result was already read once. Can be used to check if the result was already read before starting a new measurement. If not it returns `false`.
### getResult()
Returns the result of the last measurement.

## Example Program
```
#include "analogReader.h"
#define A_PIN A0

void setup() {
  Serial.begin(9600);
  analogReader::setup();
  analogReader::startMeasurement(A_PIN);
}

void loop() {
  if(analogReader::resultAvailable()) {
    Serial.println(analogReader::getResult());
    analogReader::startMeasurement(A_PIN);
  }
}
```
