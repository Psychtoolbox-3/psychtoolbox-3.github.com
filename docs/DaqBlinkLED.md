# [DaqBlinkLED](DaqBlinkLED)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

err=[DaqBlinkLED](DaqBlinkLED)[(DeviceIndex)]((DeviceIndex))  
USB-1208FS: blink LED.  
"[DeviceIndex](DeviceIndex)" is a small integer, the array index specifying which HID  
      device in the array returned by [PsychHID](PsychHID)('Devices') is interface 0  
      of the desired USB-1208FS box.  
See also Daq, [DaqFunctions](DaqFunctions), [DaqPins](DaqPins), [DaqTest](DaqTest), [PsychHIDTest](PsychHIDTest).  
  
4/15/05 dgp Wrote it.  
11/13/07  mpr Tested it on USB-1608FS called by Matlab 2007b from a Mac  
                  Pro running Leopard.  Worked with no changes!   
1/10/08   mpr worked to get improved internal consistency (changed  
                  "device" to "daq", fixed "[DaqTest](DaqTest)" and "[PsychHIDTest](PsychHIDTest)"  
5/22/08   mk  Add (untested!) support for USB-1024LS box.   
5/23/08   mk  Add caching for HID device list.   




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqBlinkLED.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqBlinkLED.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqBlinkLED.m</code>
</div>

