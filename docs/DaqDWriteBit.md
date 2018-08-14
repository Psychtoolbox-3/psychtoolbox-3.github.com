# [DaqDWriteBit](DaqDWriteBit)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

err=[DaqDReadBit](DaqDReadBit)[(DeviceIndex]((DeviceIndex),[BitNumber](BitNumber),value)  
USB-1608FS: Write bit to digital port.   
"[DeviceIndex](DeviceIndex)" is a small integer, the array index specifying which HID  
      device in the array returned by [PsychHID](PsychHID)('Devices') is interface 0  
      of the desired USB-1608FS box.  
  
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
\*                                                                            \*  
\* If your Daq is a USB-1208FS or USB-1408FS, this code has not been tested;  \*  
\* it probably will not run on your device.  The USB-1608FS has only one DIO  \*  
\* port and that is what this code was written to expect.  To make it run on  \*  
\* a 12 or 14 bit device, you should fix this to take an additional input     \*  
\* (the portnumber) and to continue to behave as is for the 16-bit device.    \*  
\* An example of how to do that can be found in [DaqDConfigPort](DaqDConfigPort).  -- mpr       \*  
\*                                                                            \*  
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
  
[BitNumber](BitNumber) should range from 0:7 specifying the channel whose bit you want set;  
0 corresponds to screw terminal 21, 1 corresponds to screw terminal 23, etc.  
"value" should be 0 or 1.  
  
[BitNumber](BitNumber) can be a vector in order to write multiple bits at once.  To  
implement this, value must be a vector the same length as [BitNumber](BitNumber), or it  
must be a scalar in which case all designated bits will be given that value.  
  
See also Daq, [DaqFunctions](DaqFunctions), [DaqPins](DaqPins), [DaqTest](DaqTest), [PsychHIDTest](PsychHIDTest),  
[DaqDConfigPortBit](DaqDConfigPortBit), [DaqDReadBit](DaqDReadBit), [DaqDeviceIndex](DaqDeviceIndex), [DaqDIn](DaqDIn), [DaqDOut](DaqDOut).  
  
12/17/07 mpr scavenged code from [DaqDOut](DaqDOut) and edited it to make this  
1/11/08  mpr  swept through attempting to improve consistency across daq  
                  functions  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqDWriteBit.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqDWriteBit.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqDWriteBit.m</code>
</div>

