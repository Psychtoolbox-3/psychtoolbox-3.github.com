# [RaspberryPiGPIODemo](RaspberryPiGPIODemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[RaspberryPiGPIODemo](RaspberryPiGPIODemo) - Show basic use of GPIO's on [RaspberryPi](RaspberryPi).  
  
Demos full access to the Pi [GPIOs](GPIOs) when running as root,  
slightly more limited access when running as a regular user,  
and also the different setup steps required.  
  
Accessing the [GPIOs](GPIOs) as non-root requires the user account  
to be a member of the Unix group 'gpio'. [PsychLinuxConfiguration](PsychLinuxConfiguration)  
should take care of adding your account if you let it do that  
setup for you. The 'gpio' command line utility allows to configure  
aspects of the [GPIOs](GPIOs) which your code can't control as non-root,  
therefore you'll see multiple system() callouts in this script  
to that helper utility. If the [RPiGPIOMex](RPiGPIOMex) mex file doesn't work  
then you will need to install the 'wiringPi' package to provide  
the required libwiringPi runtime library.  
  
Shows digital i/o by flashing/alternating the two  
[LEDs](LEDs) on the [RPi](RPi) 2B, Red power, and green status.  
  
Shows how to efficiently wait for a rising edge  
trigger on Broadcom pin 17, a real GPIO pin on the  
connector. To avoid the need to actually connect  
a switch to the connector, uses internal programmable  
pullup and pulldown resistors to simulate external  
trigger input to the pin.  
  
Please note that the [RPiGPIOMex](RPiGPIOMex) file is just meant as  
a temporary stop-gap solution to get things going, until  
PTB gains a universal I/O driver. Development and support  
of [RPiGPIOMex](RPiGPIOMex) may cease at a future point in time, it may  
even get removed from the distro! Plan accordingly, maybe  
use a M-File wrapper around it to simplify transition to a  
future better I/O driver.  
  
All pin numbers used with [RPiGPIOMex](RPiGPIOMex) are Broadcom GPIO pin  
numbers, not pin numbers on the connector or wiringPi pin numbers!  
  
A nice translation table between connector pins and Broadcom GPIO  
pins can be found on the following website: https://pinout.xyz  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/RaspberryPiGPIODemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/RaspberryPiGPIODemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/RaspberryPiGPIODemo.m</code>
</div>

