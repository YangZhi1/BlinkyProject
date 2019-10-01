## Update 1 Changes (1/10/2019)
- Removed P10 (Sum) and P12 (Carry Out)

- Changed name of output (to pin_OutOne/Two/Three) in custom.ucf file (Added the instantiation of these outputs in module mojo_top)

- Stopped using blinker.luc in mojo_top.luc (main file), since we do not need a blinking LED anymore


# BlinkyProject
Want to make certain LEDs on your MOJO blink? Just clone this repo!


## Instructions:
Pin Locations (On your MOJO IO Shield):

(Input) P2 - A (Connect this in parallel to A before it passes through switch on stripboard)

(Input) P6 - B (Connect this in parallel to B before it passes through switch on stripboard)

(Input) P8 - Carry In (Connect this in parallel to Carry In before it passes through switch on stripboard)

(Output) P51 - FPGA Output A (Connect this in parallel to A before it passes through switch on stripboard)

(Output) P41 - FPGA Output B (Connect this in parallel to B before it passes through switch on stripboard)

(Output) P35 - FPGA Output Carry In (Connect this in parallel to B before it passes through switch on stripboard)

### How to make it work:
Connect P2 and P51 in parallel to (before)switch A

Connect P6 and P41 in parallel to (before)switch B

Connect P8 and P35 in parallel to (before)switch Carry In


### On MOJO:
Look at the 3 rows of 8 LEDs on your MOJO (Labelled 0-23)

LED0 - A

LED1 - B

LED2 - Carry In

LED5 - Sum (The actual correct sum given the FPGA output)

LED6 - Carry Out (The actual correct Carry Out given the FPGA output)

*You don't really need LED3 and LED4 because they should already be shown on your stripboard by the LED colour of your choice*


## How it works:
Your digital outputs from the FPGA (51, 41, 35) are connected in parallel to the digital inputs (2, 6, 8).

2, 6, 8 are responsible for lighting up LED0, LED1, LED2 respectively. The correct sum and carry (using logic from the Lucid program) will be displayed on LED5 and LED6.

Compare LED5 and LED6 to the LEDs you have on your stripboard

### Self-made error:
Leave any of the switch A, B, or C off and you can see the difference on the stripboard (Wrong in this case) vs on the Mojo (Correct one)
