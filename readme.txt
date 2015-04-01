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

These are the settings of a Stock MaxNC10-2 machine.  I have verified that these settings on my machine.

**** Connected to COM4 @ 115200 baud ****

Grbl 0.9i MaxNC10 ['$' for help]
G20G90ok
>>> $$
$0=50 (step pulse, usec)
$1=50 (step idle delay, msec)
$2=0 (step port invert mask:00000000)
$3=0 (dir port invert mask:00000000)
$4=0 (step enable invert, bool)
$5=0 (limit pins invert, bool)
$6=0 (probe pin invert, bool)
$10=3 (status report mask:00000011)
$11=0.020 (junction deviation, mm)
$12=0.002 (arc tolerance, mm)
$13=1 (report inches, bool)
$20=0 (soft limits, bool)
$21=0 (hard limits, bool)
$22=0 (homing cycle, bool)
$23=0 (homing dir invert mask:00000000)
$24=127.000 (homing feed, mm/min)
$25=127.000 (homing seek, mm/min)
$26=250 (homing debounce, msec)
$27=1.000 (homing pull-off, mm)
$100=314.961 (x, step/mm)
$101=314.961 (y, step/mm)
$102=314.961 (z, step/mm)
$110=381.000 (x max rate, mm/min)
$111=381.000 (y max rate, mm/min)
$112=381.000 (z max rate, mm/min)
$120=5.000 (x accel, mm/sec^2)
$121=5.000 (y accel, mm/sec^2)
$122=5.000 (z accel, mm/sec^2)
$130=200.000 (x max travel, mm)
$131=200.000 (y max travel, mm)
$132=200.000 (z max travel, mm)
ok
>>> $n
$N0=G20G90
$N1=
ok


Hope this helps somebody else out.
Bruce
