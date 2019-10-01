# BlinkyProject
Want to make certain LEDs on your MOJO blink? Just clone this repo!


## Instructions:
Pin Locations (On your MOJO IO Shield):

P2 - A

P6 - B

P8 - Carry In

P10 - Sum

P12 - Carry Out

P51 - FPGA Output A

P41 - FPGA Output B

P35 - FPGA Output Carry In

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
