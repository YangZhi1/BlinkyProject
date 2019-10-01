# BlinkyProject
Want to make certain LEDs on your MOJO blink? Just clone this repo!


## Instructions:
Pin Locations (On your MOJO IO Shield):

P2 - A (Connect this in parallel to A before it passes through switch on stripboard)

P6 - B (Connect this in parallel to B before it passes through switch on stripboard)

P8 - Carry In (Connect this in parallel to Carry In before it passes through switch on stripboard)

P10 - Sum

P12 - Carry Out

P51 - FPGA Output A (Connect this in parallel to A before it passes through switch on stripboard)

P41 - FPGA Output B (Connect this in parallel to B before it passes through switch on stripboard)

P35 - FPGA Output Carry In (Connect this in parallel to B before it passes through switch on stripboard)

P.S. Just leave P40 alone cause I wanted to try slowing down the blink time

### How to make it work:
Connect P2 - P51

Connect P6 - P41

Connect P8 - P35


Connect P10 in parallel to the wire to *sum* on your stripboard

Connect P12 in parallel to the wire to *carry out* on your stripboard

### On MOJO:
Look at the 3 rows of 8 LEDs on your MOJO (Labelled 0-23)

LED0 - A

LED1 - B

LED2 - Carry In

LED3 - Sum (The one connected in parallel to stripboard's Sum)

LED4 - Carry Out (The one connected in parallel to stripboard's Carry Out)

LED5 - Sum (The actual correct sum given the FPGA output)

LED6 - Carry Out (The actual correct Carry Out given the FPGA output)

*You don't really need LED3 and LED4 because they should already be shown on your stripboard by the LED colour of your choice*


## How it works:
Your digital outputs from the FPGA (51, 41, 35) are connected in parallel to the digital inputs (2, 6, 8).

2, 6, 8 are responsible for lighting up LED0, LED1, LED2 respectively. The correct sum and carry (using logic from the Lucid program) will be displayed on LED5 and LED6.

Compare LED5 and LED6 to the LEDs you have on your stripboard

### Self-made error:
Leave any of the switch A, B, or C off and you can see the difference on the stripboard (Wrong in this case) vs on the Mojo (Correct one)
