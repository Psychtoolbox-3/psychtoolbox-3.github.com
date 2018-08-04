# [CMCheckInit](CMCheckInit)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[CMCheckInit](CMCheckInit)([meterType], [[PortString](PortString)])  
  
Initialize the color meter. The routine calls the  
lower level routines for given 'meterType'. If the low level routine  
fails, this routine retries, then prompts the user to take appropriate  
action. If the low level routine succeeds, this  
routine is silent.  
  
### The following colormeters are supported:  
  
meterType 1 is the PR650 (default)  
meterType 2 is the CVI (need [CVIToolbox)](CVIToolbox)) - Not yet implemented!  
meterType 3 is the CRS Colorimeter  
meterType 4 is the PR655  
meterType 5 is the PR670  
meterType 6 is the PR705  
  
For the PR-series colorimeters, 'PortString' is the optional name of a  
device string for the serial port or Serial-over-USB port to which the  
device is connected. If none is given, the routine uses different files  
and built-in defaults to try to find the proper port: If there is a file  
'CMPreferredPort.txt' in the search path of Matlab/Octave, it will parse  
that file for a [PortString](PortString) to use. Else it will use a hard-coded default  
inside this routine.  
  
If a calibration file with name 'PRXXXPorts' for the PR-XXX exists,  
it will override what is in [CMPrefferedPort](CMPrefferedPort).txt.  There are two  
possible formats for the structure in this file.  
  If the structure has a [PortString](PortString) field, this is passed to  
  routine [FindSerialPort](FindSerialPort) to get the actual port.  Otherwise,  
  if the structure has a .in field, this string is used directly.  
  
Other Colorimeters, e.g., CRS [ColorCal](ColorCal), have their own specific setup  
methods and this routine just calls their setup code with default  
settings.  
  
9/15/93 dhb       Modified to use new [CMInit](CMInit) properly.  
1/18/94 jms       Added gHardware switch  
1/24/94 dhb       Changed sign of gHardware switch.  
2/20/94 dhb       Call through CMETER rather than CM... routines.  
4/4/00  dhb       Optional port name, only used on SERIAL version.  
9/11/00 dhb       Added meterType.  
1/4/02  dhb, ly   Try to get OS9 version to work with Megawolf board and SERIAL.  
1/10/02 dhb, ly   Change calling convention.  Remove passing of port, but read  
                  port from a "calibration" file in [PsychCalLocalData](PsychCalLocalData) if it's there.  
4/13/02 dgp       Cosmetic.  
2/26/03 dhb       Add CRS Colorimeter, change meter type of PR-650 to 1.  
10/05/06 dhb, cgb OSX version.  
11/27/07 mpr      replaced hard coded portNameIn with [FindSerialPort](FindSerialPort) for OS X, and  
                  attempted to make this more robust and user-friendly.  
                  modifications tested only on Mac OS 10.5.1, Matlab 2007b, on  
                  a Mac Pro.  Other systems may require more tinkering...  
2/07/09  mk, tbc  Add PR-655 support.  
2/07/09  mk       Add experimental setup code for use of [IOPort](IOPort) instead of [SerialComm](SerialComm).  
2/11/09  cgb,mk   Small fixes: Now we use [IOPort](IOPort) instead of [SerialComm](SerialComm) --  
                  by default. Verified to work for both PR650 and PR655 toolboxes.  
7/16/12  dhb      Choose right global default for 64-bit Matlab.  Hope I  
                  did this in a way that doesn't break anything else.  
7/20/12  dhb      Undid 7/16/12 change.  Error was due to a stale [IOPort](IOPort) on my path  
12/04/12 zlb      Adding PR-705 support.  
4/10/13  dhb      More flexible behavior supported via [PRXXXPorts](PRXXXPorts) calibration file.  
1/25/13  dhb, ms  More info printed on failure for PR-670 case.  Trying to track down intermittant  
                  failures to initialize when routine is called multiple times in a long calibration loop.  
6/11/17  mk       Remove dead [SerialComm](SerialComm)() driver path.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/CMCheckInit.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/CMCheckInit.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/CMCheckInit.m</code>
</div>

