#include <FastLED.h>

// How many leds in your strip?
#define NUM_LEDS 11

// For led chips like WS2812, which have a data line, ground, and power, you just
// need to define DATA_PIN.  For led chipsets that are SPI based (four wires - data, clock,
// ground, and power), like the LPD8806 define both DATA_PIN and CLOCK_PIN
// Clock pin only needed for SPI based chipsets when not using hardware SPI
#define DATA_PIN 12
#define CLOCK_PIN 13

// Define the array of leds
CRGB leds[NUM_LEDS];

void setup() { 
    FastLED.addLeds<NEOPIXEL, DATA_PIN>(leds, NUM_LEDS);  // GRB ordering is assumed
}

void loop() {
  int i=0;
  for (i=0; i<NUM_LEDS; i++)
  {

  leds[i] = CRGB::Red;
  leds[i+1] = CRGB::Green;
  leds[i+2] = CRGB::Blue;
  FastLED.show();
  delay(100);
  // Now turn the LED off, then pause
  leds[i] = CRGB::Blue;
  FastLED.show();
  
  }

С одним из циклов ниже лампа могла бы работать, но циклы не выполняются
1) int i=0;

for (i=0; i<NUM_LEDS; i=i+3)
{leds[i] = CRGB::Red;
  delay(500);
  leds[i] = CRGB::Black;
  printf(i);
 FastLED.show(); 
}


for (i=0; i<NUM_LEDS; i=i+3)
{leds[i+1] = CRGB::Green;
  delay(500);
  leds[i+1] = CRGB::Black;
  FastLED.show();
}

for (i=0; i<NUM_LEDS; i=i+3)
{leds[i+2] = CRGB::Blue;
  delay(500);
  leds[i+2] = CRGB::Black;
  FastLED.show();
}

2)
  for (i=0; i<NUM_LEDS; i++) 
  { 
    if (i%3 == 0)
    {leds[i] = CRGB::Red;
  delay(500);
  leds[i] = CRGB::Black;
  FastLED.show();}
delay(100);

   if (i%3 == 1)
    {leds[i+1] = CRGB::Green;
  delay(500);
  leds[i+1] = CRGB::Black;
FastLED.show();}

delay(100);

  if (i%3 == 2)
    {leds[i+2] = CRGB::Blue;
  delay(500);
  leds[i+2] = CRGB::Black;
FastLED.show();}

  delay(100);
  }