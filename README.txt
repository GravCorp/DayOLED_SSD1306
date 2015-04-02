This is a library for our Monochrome OLEDs based on SSD1306 drivers

  Pick one up today in the adafruit shop!
  ------> http://www.adafruit.com/category/63_98

These displays use SPI to communicate, 4 or 5 pins are required to  
interface

Adafruit invests time and resources providing this open source code, 
please support Adafruit and open-source hardware by purchasing 
products from Adafruit!

Written by Limor Fried/Ladyada  for Adafruit Industries.  
Scrolling code contributed by Michael Gregg
BSD license, check license.txt for more information
All text above must be included in any redistribution
--------------------------------------------------------------------------------------------
DayOLED_SSD1306 - Arduino Due library for interfacing with SSD1306-based OLEDs using DMA

Modified by Lewin Day for Grav Corp, 2015

Based on Adafruit_SSD1306 library, and using DMA SPI routines
from Marek Buriak's ILI9341_Due library, based on William Greiman's Arduino SdSpi library.
Utilise with Adafruit-GFX-Library. 

Sources for this library can be found at https://github.com/GravCorp/DayOLED_SSD1306

Connect your SSD1306 screen to the Arduino Due using the hardware SPI pins. For DC, CS, and reset,
use the digital pins of your choice. Most should work. In the example we use 11, 10 and 12.

The library is setup by default for 128x64 screens. There is a #define that can be changed 
in DayOLED_SSD1306.h to allow the use of a 128x32 or 96x16 screen.

This library makes display() calls around 4x faster for the same SPI clock speed as the hardware SPI
implementation in the Adafruit_SSD1306 library. However, running at max feasible clock (divider set to 2),
this library is ~8 times faster on display() calls, as the stock Adafruit_SSD1306 library uses a divider of 5.
If you need to change the divider for any reason (default is 2), it's line 51 of DayOLED_SSD1306.h. You might
have to slow it down for dodgy breadboard installations, etc. by choosing a higher divider.

NOTE: This library prevents and precludes use of the standard SPI library, and you should not use SPI.h with any
code that you use this library with. There'll be conflicts. If you wish to use other devices on SPI with this library,
you must use calls to fastSPIwrite() and spiRead(). For beginners, just assume you can't use other devices with this library,
just the screen, nothing else on SPI with it. For the pros, dig through and see if you can figure it out. This is an area
I am working on currently improving. It may be bugged out completely, currently.

Place the DayOLED_SSD1306 library folder your <arduinosketchfolder>/libraries/ folder. You may need to create the libraries subfolder if its your first library. Restart the IDE.

You will also have to download the Adafruit GFX Graphics core which does all the circles, text, rectangles, etc. You can get it from
https://github.com/adafruit/Adafruit-GFX-Library
and download/install that library as well.