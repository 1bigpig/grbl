This is a hack to enable grbl .9i to drive a stock pre-2004 MaxNC 10 milling machine using phase drive stepper commands.
ALL "D" pins (D2-D13) are used to control the phases of the stepper driver.  
//My MaxNC 10-2 phase driver PIN CONFIGURATION 

//Z D2-D5

//X D6-D9

//Y D10-D13

The sequence is half-stepping and is directionally correct for my machine.

This "hack" is based on the nullsub grbl fork created on Aug 2, 2012.

My hack is more of a butchering job with an axe, as all the nice things that were added in .9i (spindle control, homing
and limit switches) had to be disabled as ALL those pins are required for phase signals.  
What IS left is all of PortC (Arduino analog pins) support.  So coolant, E-stop, and even probing should still work! --currently unverified--

The phase sequence was left in long-hand code, so that it would be easy to modify for another phase driver.

For a MaxNC10 machine, my Arduino to DB25 was wired:
Arduino pin - DB25 pin (female connector)
D2  - 2
D3  - 3
D4  - 4
D5  - 5
D6  - 6
D7  - 7
D8  - 8
D9  - 9
D10 - 1
D11 - 14
D12 - 16
D13 - 17
A5  - 13
GND - 18

Hope this helps somebody else out.
Bruce
