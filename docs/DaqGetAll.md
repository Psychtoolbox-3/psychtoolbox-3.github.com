# [DaqGetAll](DaqGetAll)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

data=[DaqGetAll](DaqGetAll)[(DeviceIndex)]((DeviceIndex))  
USB-1208FS: Retrieve all analog and digital input values. This command  
reads the value from all analog input channels and digital I/Os.  
"[DeviceIndex](DeviceIndex)" is a small integer, the array index specifying which HID  
      device in the array returned by [PsychHID](PsychHID)('Devices') is interface 0   
      of the desired USB-1208FS box.  
data.analog is a 1x16 array of the values read from the analog input  
      channels.  
data.digital(1) is the value (0 to 255) read from digital port A.  
data.digital(2) is the value (0 to 255) read from digital port B.  
See also Daq, [DaqFunctions](DaqFunctions), [DaqPins](DaqPins), [DaqTest](DaqTest), [PsychHIDTest](PsychHIDTest).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqGetAll.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqGetAll.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqGetAll.m</code>
</div>

