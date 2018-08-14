# [DaqDReadBit](DaqDReadBit)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

[BitValue](BitValue)=[DaqDReadBit](DaqDReadBit)[(DeviceIndex]((DeviceIndex),[BitNumber)](BitNumber))  
USB-1608FS: Write digital port. This command writes data to the DIO port  
bits that are configured as outputs.  
"[DeviceIndex](DeviceIndex)" is a small integer, the array index specifying which HID  
      device in the array returned by [PsychHID](PsychHID)('Devices') is interface 0  
      of the desired USB-1608FS box.  
"[BitNumber](BitNumber)" an integer from 0 to 8 specifying which bit to read  
See also Daq, [DaqFunctions](DaqFunctions), [DaqPins](DaqPins), [DaqTest](DaqTest), [PsychHIDTest](PsychHIDTest).  
[DaqDeviceIndex](DaqDeviceIndex), [DaqDIn](DaqDIn), [DaqDOut](DaqDOut), [DaqAIn](DaqAIn), [DaqAOut](DaqAOut), [DaqAInScan](DaqAInScan),[DaqAOutScan](DaqAOutScan).  
  
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
  
I suspect that to get this code to work for a 1208FS or 1408FS you would have  
to modify the [SetReport](SetReport) call to add the port number (0 or 1) before   
[BitNumber](BitNumber).  Hopefully that would be all it would take, but since I don't   
have one of those devices to test, I have not implemented that fix.  Look at   
the code in [DaqDOut](DaqDOut) to see how you might code something that tested for  
whether your Daq has two DIO ports, and how you'd handle input and report to  
accommodate the added port.  
  
[BitNumber](BitNumber) can be a vector so that you can read multiple bits at once.  
  
12/xx/07 mpr scavenged code from [DaqDIn](DaqDIn) and converted it to this.  
1/11/08  mpr  swept through attempting to improve consistency across daq  
                  functions  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqDReadBit.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqDReadBit.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqDReadBit.m</code>
</div>

