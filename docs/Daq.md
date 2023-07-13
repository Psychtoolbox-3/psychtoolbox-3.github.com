# [Daq](Daq)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

Psychtoolbox/[PsychHardware](PsychHardware)/Daq/  
The Daq Toolbox  
Control a USB-1024LS, USB-1208FS, USB-1408FS, or USB-1608FS data acquisition device.  
  
The Daq Toolbox is a set of functions providing communication with  
a particular USB data acquisition device (daq): the USB-1208FS made by  
Measurement Computing (see URL below). This daq costs $150 and offers "50  
kHz" input and output 12-bit sampling of analog voltages (8 in, 2 out)  
and 16 digital i/o lines, with signals brought out to screw terminals.  
("50 kHz" is a theoretical upper limit: as of 18 April 2005 we attain 2  
kHz. See [DaqTest](DaqTest).) The USB-1208FS is the size of a wallet and is powered  
through its USB cable. We have complete control of it from within Matlab or,  
Octave via the [PsychHID](PsychHID) extension.   
  
There is a Daq M file (see [DaqFunctions)](DaqFunctions)) for each USB-1208FS firmware  
command, plus a few more to facilitate use of the device.   
  
There is a near-perfect isolation of the dependency on platform and  
device at the two levels of code in the Daq Toolbox. The [PsychHID](PsychHID) MEX  
file (written in C) is highly dependent on the platform, but  
independent of the particular HID-compliant device. It provides generic  
HID commands. (HID, or Human Interface Device, is a USB class specifying  
a communication protocol for the device and host.) The Daq M files are  
specific to our HID-compliant device, the USB-1208FS, but independent of  
the platform, and would run unchanged in MATLAB or Octave on any other  
computer for which we provided the [PsychHID](PsychHID) extension. We hope that users  
of the Psychtoolbox will find it easy to write new MATLAB M files  
using [PsychHID](PsychHID) to support other HID-compliant devices, using the Daq  
Toolbox as a model.  
  
NOT RESPONDING? If [PsychHID](PsychHID) is not responding, e.g. after unplugging it   
and plugging it back in, try quitting and restarting MATLAB or Octave.  
We find that this reliably restores normal communication.   
  
LINUX: If you want to use these functions without the need to run  
Matlab or Octave as root user (i.e., without need for root login or the  
sudo command), you have to run the script [PsychLinuxConfiguration](PsychLinuxConfiguration) once.  
This happens automatically during invocation of [DownloadPsychtoolbox](DownloadPsychtoolbox),  
[UpdatePsychtoolbox](UpdatePsychtoolbox), or [SetupPsychtoolbox](SetupPsychtoolbox), but if you didn't install  
Psychtoolbox by one of these means, you'll need to run it manually.  
Then after unplugging and replugging your device, non-root access should  
work.  
  
Denis Pelli, 30 April 2005.  
  
From November 2007 through January 2008, the functions in this toolbox   
were tested with a USB-1608FS.  There are significant hardware  
differences between the two devices, notably one Digital I/O port vs. two  
and no analog output ports in the 1608.  Nevertheless, most of the  
command codes are the same, so the two devices can share a lot of common  
software.  The USB-1608FS was connected to a Mac Pro running Leopard for  
most tests (some tests also run with Tiger; no significant performance  
differences were found in those cases).  If you have a 1608 and have  
trouble running any of the code here, you might try e-mailing  
[MickeyPRowe](MickeyPRowe)@gmail.com.  
  
Mickey P. Rowe, 10 January 2008.  
  
From August 2011 on, these functions should also work on MS-Windows and  
GNU/Linux, due to the availability of [PsychHID](PsychHID) for these platforms.  
  
Mario Kleiner, 15 August 2011.  
  
  
web http://www.measurementcomputing.com/cbicatalog/directory.asp?dept\_id=403 -browser;  
web http://psychtoolbox.org/daq.html -browser;  
See also: [DaqFunctions](DaqFunctions), [DaqTest](DaqTest), [PsychHIDTest](PsychHIDTest), [PsychHID](PsychHID),  
[PsychHardware](PsychHardware), [DaqPins](DaqPins), [DaqCalls](DaqCalls), [DaqCodes](DaqCodes),  
[DaqDeviceIndex](DaqDeviceIndex), [DaqFind](DaqFind), [DaqDIn](DaqDIn), [DaqDOut](DaqDOut), [DaqAIn](DaqAIn), [DaqAOut](DaqAOut), [DaqAInScan](DaqAInScan), [DaqAOutScan](DaqAOutScan).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/Contents.m</code>
</div>

{{category}}