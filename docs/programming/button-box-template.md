# Button Box Code Template

This is a general outline for creating an X-Input emulator with a Teensy Arduino Board

## What you Will Need
  - 32 Bit PJRC Teensy (or clone) with USB Support
  - Arduino IDE with Teensyduino installed
  - Buttons!

## Code
This code is a template from the Teensyduino library with USB Joystick support, it should work out of the box with Teensyduino. This assigns DIO pins 1-9 as X-Input buttons that should be discovered as a controller on code upload. This will work out of the box with Driver Station because it is emulating an Xbox controller.

<details open>
<summary>CPP Example Code</summary>

```cpp
//This code is in C++ and is for coding a button box using Arduino IDE 
//As of now (2025) we are using a Teensy 3.2 Board and using Teensyduino 
//with Arduino IDE

//This is the code
//Source: https://www.partsnotincluded.com/how-to-emulate-an-xbox-controller-with-arduino-xinput/ 
//This is a modified version of the USB_Joystick Button Example code

/* Buttons to USB Joystick Example

   You must select Joystick from the "Tools > USB Type" menu

   This example code is in the public domain.
*/

#include <Bounce.h>

// Create Bounce objects for each button.  The Bounce object
// automatically deals with contact chatter or "bounce", and
// it makes detecting changes very simple.
Bounce button1 = Bounce(1, 10);  // 10 = 10 ms debounce time
Bounce button2 = Bounce(2, 10);  // which is appropriate for
Bounce button3 = Bounce(3, 10);  // most mechanical pushbuttons
Bounce button4 = Bounce(4, 10);
Bounce button5 = Bounce(5, 10);
Bounce button6 = Bounce(6, 10);
Bounce button7 = Bounce(7, 10);
Bounce button8 = Bounce(8, 10);
Bounce button9 = Bounce(9, 10);

void setup() {
  // Configure the pins for input mode with pullup resistors.
  // The pushbuttons connect from each pin to ground.  When
  // the button is pressed, the pin reads LOW because the button
  // shorts it to ground.  When released, the pin reads HIGH
  // because the pullup resistor connects to +5 volts inside
  // the chip.  LOW for "on", and HIGH for "off" may seem
  // backwards, but using the on-chip pullup resistors is very
  // convenient.  The scheme is called "active low", and it's
  // very commonly used in electronics... so much that the chip
  // has built-in pullup resistors!
  pinMode(1, INPUT_PULLUP);
  pinMode(2, INPUT_PULLUP);
  pinMode(3, INPUT_PULLUP);
  pinMode(4, INPUT_PULLUP);
  pinMode(5, INPUT_PULLUP);
  pinMode(6, INPUT_PULLUP);  // Teensy++ LED, may need 1k resistor pullup
  pinMode(7, INPUT_PULLUP);
  pinMode(8, INPUT_PULLUP);
  pinMode(9, INPUT_PULLUP);

  // Please be aware the X, Y, Z, Zr and Slider axes will have default
  // settings, if you only use the buttons.  This can give the appearance
  // of the buttons interfering with the axes, if your PC software shows
  // different default assumed values before your first button press.
  //  More details here:
  //  https://forum.pjrc.com/threads/29320-Teensy-3-1-Button-problems?p=80275#post80275
}

void loop() {
  // Update all the buttons.  There should not be any long
  // delays in loop(), so this runs repetitively at a rate
  // faster than the buttons could be pressed and released.
  button1.update();
  button2.update();
  button3.update();
  button4.update();
  button5.update();
  button6.update();
  button7.update();
  button8.update();
  button9.update();

  // Check each button for "falling" edge.
  // Update the Joystick buttons only upon changes.
  // falling = high (not pressed - voltage from pullup resistor)
  //           to low (pressed - button connects pin to ground)
  if (button1.fallingEdge()) {
    Joystick.button(1, 1);
  }
  if (button2.fallingEdge()) {
    Joystick.button(2, 1);
  }
  if (button3.fallingEdge()) {
    Joystick.button(3, 1);
  }
  if (button4.fallingEdge()) {
    Joystick.button(4, 1);
  }
  if (button5.fallingEdge()) {
    Joystick.button(5, 1);
  }
  if (button6.fallingEdge()) {
    Joystick.button(6, 1);
  }
  if (button7.fallingEdge()) {
    Joystick.button(7, 1);
  }
  if (button8.fallingEdge()) {
    Joystick.button(8, 1);
  }
  if (button9.fallingEdge()) {
    Joystick.button(9, 1);
  }

  // Check each button for "rising" edge
  // Update the Joystick buttons only upon changes.
  // rising = low (pressed - button connects pin to ground)
  //          to high (not pressed - voltage from pullup resistor)
  if (button1.risingEdge()) {
    Joystick.button(1, 0);
  }
  if (button2.risingEdge()) {
    Joystick.button(2, 0);
  }
  if (button3.risingEdge()) {
    Joystick.button(3, 0);
  }
  if (button4.risingEdge()) {
    Joystick.button(4, 0);
  }
  if (button5.risingEdge()) {
    Joystick.button(5, 0);
  }
  if (button6.risingEdge()) {
    Joystick.button(6, 0);
  }
  if (button7.risingEdge()) {
    Joystick.button(7, 0);
  }
  if (button8.risingEdge()) {
    Joystick.button(8, 0);
  }
  if (button9.risingEdge()) {
    Joystick.button(9, 0);
  }
}
```
</details>

## Wiring
By default, the above code uses DIO pins 1-9 on any given Teensy board, and so the buttons should be wired to a common ground (GND) on one side, and any of the pins 1-9 on the opposite contact of the button. The code automatically handles debouncing, meaning the only necessary wiring is directly from the button to ground on one side and to the DIO pin on the other side.xw