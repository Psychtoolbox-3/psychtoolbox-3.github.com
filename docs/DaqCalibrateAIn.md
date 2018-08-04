# [DaqCalibrateAIn](DaqCalibrateAIn)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

Syntax: [DaqCalibrateAIn](DaqCalibrateAIn)[(DeviceID]((DeviceID),[AnalogChannel)](AnalogChannel))  
  
Purpose: Measure output of calibration pin to provide calibration of the  
          input "[AnalogChannel](AnalogChannel)" on the device "[DeviceID](DeviceID)".  
  
History:  1/10/08   mpr   decided to calibrate good times come on!  
          3/5/08    mpr   fixed bug exposed when preference file doesn't exist  
  
This function was written for the USB-1608FS.  It could be easily modified for  
a 1208FS, but since there are only two levels of the output on that device it  
seems like it would be a bit less useful.  If you want to modify this for such  
a device, please feel free.  Since I don't have one, I'm not motivated...   
If you have a 1608FS, this function walks through the outputs of the  
calibration terminal and the gain settings of the analog channel and produces  
corrections that will affect the interpretation of numbers derived from other  
functions (e.g., [DaqAIn](DaqAIn) and [DaqAInScan)](DaqAInScan)).  "[AnalogChannel](AnalogChannel)" can be a vector  
(values range from 0:7) if you want to calibrate multiple channels at once.  
Default channel is 0, and if no argument is passed for [DeviceID](DeviceID), [DaqFind](DaqFind) will  
be run to see if you have only one device.  -- mpr  
  
To calibrate a channel, connect the appropriate pin(s) to pin 17.  For channel  
0, you want pin 1 to pin 17, for channel 1, pin 3 to pin 17, for channel 2,  
pin 5 to... you probably see the pattern...  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqCalibrateAIn.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqCalibrateAIn.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqCalibrateAIn.m</code>
</div>

