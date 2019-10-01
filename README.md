## Update 1 Changes (1/10/2019)
- Removed P10 (Sum) and P12 (Carry Out)

- Changed name of output (to pin_OutOne/Two/Three) in custom.ucf file (Added the instantiation of these outputs in module mojo_top)

- Stopped using blinker.luc in mojo_top.luc (main file), since we do not need a blinking LED anymore

## Update 2 Changes (1/10/2019 21:38)
- Removed P2 P6 P8 (Input readings for A, B and C) cause I realised that I'm taking in an input reading from an output by the same device, which I could just program in Lucid to save works on hardware.

- 


# BlinkyProject
Want to make certain LEDs on your MOJO blink? Just clone this repo!


## Instructions:
Pin Locations (On your MOJO IO Shield):

(Output) P51 - FPGA Output A (Connect this in parallel to A before it passes through switch on stripboard)

(Output) P41 - FPGA Output B (Connect this in parallel to B before it passes through switch on stripboard)

(Output) P35 - FPGA Output Carry In (Connect this in parallel to B before it passes through switch on stripboard)

Switch Locations (On MOJO IO Shield):

Switch 0 - Right most switch (Controls output to A, flip up to "turn on" A)

Switch 8 - Row 2 right most Switch  (Controls output to B, flip up to "turn on" B)

Switch 16 - Row 3 right most switch (Controls output to Carry In, flip up to "turn on" Carry In)

### How to make it work:
Connecting the pins to the switch (or before the switch) will provide a current to the 1 Bit Full Adder Circuit (so you don't have to put any batteries in for the FPGA testing). You can control whether current passes through them using the switches as stated above.

Connect P51 in parallel to (before)switch A

Connect P41 in parallel to (before)switch B

Connect P35 in parallel to (before)switch Carry In



### On MOJO:
Look at the 3 rows of 8 LEDs on your MOJO (Labelled 0-23)

LED0 - A

LED1 - B

LED2 - Carry In

LED5 - Sum (The actual correct sum given the FPGA output)

LED6 - Carry Out (The actual correct Carry Out given the FPGA output)


## How it works:
Your digital outputs from the FPGA (51, 41, 35) are connected in parallel to switch, so you don't have to put batteries into your 1 bit full adder circuit (*for the testing using FPGA*)

2, 6, 8 are responsible for lighting up LED0, LED1, LED2 respectively. The correct sum and carry (using logic from the Lucid program) will be displayed on LED5 and LED6.

Compare LED5 and LED6 to the LEDs you have on your stripboard

### Self-made error:
Test case: 
- Flip Switch 0, 8, 16 on (By right since all are on, sum and carry out should be 1 which means that both LEDs on stripboard should light up)
- On the stripboard, off either one of switch A/B/CarryIn
- Stripboard LED should only have Carry Out lit up and. (Carry out = 1, Sum = 0) <- "Wrong" signal on your stripboard, since input is 1/1/1.
- MOJO FPGA should have LED5 and LED6 lit up (Carry out = 1, Sum = 1) <- Right signal on MOJO since input is 1/1/1.
