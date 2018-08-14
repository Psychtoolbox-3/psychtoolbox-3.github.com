# [DaqMemWrite](DaqMemWrite)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

err=[DaqMemWrite](DaqMemWrite)[(DeviceIndex]((DeviceIndex),address,data)  
USB-1208FS: Write memory. This command writes to the nonvolatile EEPROM  
memory on the device. The nonvolatile memory is used to store  
calibration coefficients, system information, and user data.  Locations  
0x000 to 0x07F are reserved for firmware use and may not be written.  
"[DeviceIndex](DeviceIndex)" is a small integer, the array index specifying which HID  
      device in the array returned by [PsychHID](PsychHID)('Devices') is interface 0  
      of the desired USB-1208FS box.  
"address" is the 16-bit start address for the write.  
"data" is a vector with length up to 59, one element per byte.  
See also [DaqWriteCode](DaqWriteCode), [DaqMemRead](DaqMemRead), Daq, [DaqTest](DaqTest), [PsychHIDTest](PsychHIDTest).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqMemWrite.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqMemWrite.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqMemWrite.m</code>
</div>

