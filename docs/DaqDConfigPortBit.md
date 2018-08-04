# [DaqDConfigPortBit](DaqDConfigPortBit)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

err=[DaqDConfigPortBit](DaqDConfigPortBit)[(DeviceIndex]((DeviceIndex),[BitNumber](BitNumber),direction)  
USB-1608FS: Configure digital port. This command sets the direction of  
the DIO port to input or output.  
"[DeviceIndex](DeviceIndex)" is a small integer, the array index specifying which HID  
      device in the array returned by [PsychHID](PsychHID)('Devices') is interface 0  
      of the desired USB-1208FS box.  
"[BitNumber](BitNumber)" ranges from 0:7 and can be a vector if you want to configure   
      multiple ports at the same time.  
"direction" 0 = output, 1 = input; must be either a scalar or a vector of the   
      same length as [BitNumber](BitNumber)  
See also Daq, [DaqFunctions](DaqFunctions), [DaqPins](DaqPins), [DaqTest](DaqTest), [PsychHIDTest](PsychHIDTest), [DaqDReadBit](DaqDReadBit),   
      [DaqDWriteBit](DaqDWriteBit), [DaqDConfigPort](DaqDConfigPort), [DaqDIn](DaqDIn), [DaqDOut](DaqDOut).  
  
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
\*                                                                            \*  
\* If your Daq is a USB-1208FS or USB-1408FS, this code has not been tested   \*  
\* probably will not run on your device.  The USB-1608FS has only one DIO     \*  
\* port and that is what this code was written to expect.  To make it run on  \*  
\* a 12 or 14 bit device, you should fix this to take an additional input     \*  
\* (the portnumber) and to continue to behave as is for the 16-bit device.    \*  
\* An example of how to do that can be found in [DaqDConfigPort](DaqDConfigPort).  -- mpr       \*  
\*                                                                            \*  
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
  
Code has not been tested on USB-1208FS or USB-1408FS.  If you have one of  
those devices, you should modify this code to accept portnumber as an  
additional input parameter.  See [DaqDConfigPort](DaqDConfigPort) for an example of how to deal  
with the added input.  
  
12/17/07  mpr scavenged and modified code from [DaqDConfigPort](DaqDConfigPort)  
1/11/08   mpr swept through trying to improve consistency across daq  
                functions  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqDConfigPortBit.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqDConfigPortBit.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqDConfigPortBit.m</code>
</div>

