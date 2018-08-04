# [DaqDOut](DaqDOut)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

err=[DaqDOut](DaqDOut)[(DeviceIndex]((DeviceIndex),port,data)  
USB-1208FS: Write digital port. This command writes data to the DIO port  
bits that are configured as outputs.  
"[DeviceIndex](DeviceIndex)" is a small integer, the array index specifying which HID  
      device in the array returned by [PsychHID](PsychHID)('Devices') is interface 0  
      of the desired USB-1208FS box.  
"port" 0 = port A, 1 = port B  
"data" 8-bit value, 0 to 255.  
  
USB-1608FS: Only has one DIO port, so second argument is irrelevant and will  
be ignored if passed.  Function will check to determine if device is a 1608,  
and act accordingly.  
  
USB-1024LS: Has three ports, numbered: 1 = port A, 4 = port B,  
10 = port C (the sum of: 8 = portC low, 2 = portC high). Maybe you'll  
need to set port C separately in two calls for low- and high- part.  
The card is verified to work well with port A or B for output.  
  
See also Daq, [DaqFunctions](DaqFunctions), [DaqPins](DaqPins), [DaqTest](DaqTest), [PsychHIDTest](PsychHIDTest).  
[DaqDeviceIndex](DaqDeviceIndex), [DaqDIn](DaqDIn), [DaqDOut](DaqDOut), [DaqAIn](DaqAIn), [DaqAOut](DaqAOut), [DaqAInScan](DaqAInScan),[DaqAOutScan](DaqAOutScan).  
  
4/15/05   dgp Wrote it.  
12/18/07  mpr Updated for use with USB-1608FS.  
1/11/08   mpr Swept through trying to improve consistency across daq  
              functions.  
5/22/08   mk  Add (untested!) support for USB-1024LS box.  
5/23/08   mk  Add caching for HID device list.  
07/31/16  mk  Remove experimental note about 1024LS. It's tested and known to work.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqDOut.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqDOut.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqDOut.m</code>
</div>

