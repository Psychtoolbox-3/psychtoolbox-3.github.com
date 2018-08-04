# [DaqDIn](DaqDIn)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

data=[DaqDIn](DaqDIn)([[DeviceIndex](DeviceIndex)],[[NumberOfPorts](NumberOfPorts)])  
USB-1208FS: Read digital ports. This command reads the current state of  
the DIO ports.  The return value will be the value seen at the port pins.  
data(1) is the 8-bit value read from port A.  
data(2) is the 8-bit value read from port B.  
"[DeviceIndex](DeviceIndex)" is a small integer, the array index specifying which HID  
      device in the array returned by [PsychHID](PsychHID)('Devices') is interface 0  
      of the desired USB-1208FS box.  
  
USB-1608FS: There is only one port, so only one meaningful return value.    
First argument is optional if you have only one DAQ device, but code will  
run faster if [DeviceIndex](DeviceIndex) is specified.  Second argument is optional; if  
it is not specified, software will attempt to determine if it should be 1  
or 2 based on the type of device.  Specifying it explicitly speeds up  
code about 1 to 2  milliseconds per call on a dual core [MacI](MacI) with 2.67  
[GHz](GHz) processors. -- mpr   
  
USB-1024LS: Has three ports, numbered: 1 = port A, 4 = port B,  
10 = port C (the sum of: 8 = portC low, 2 = portC high). Maybe you'll  
need to read port C separately in two calls for low- and high- part.  
The card is verified to work well with port C for input, not addressing  
the high and low port C separately, but the whole port C at once.  
  
See also Daq, [DaqFunctions](DaqFunctions), [DaqPins](DaqPins), [DaqTest](DaqTest), [PsychHIDTest](PsychHIDTest).  
[DaqDeviceIndex](DaqDeviceIndex), [DaqDOut](DaqDOut), [DaqAIn](DaqAIn), [DaqAOut](DaqAOut), [DaqAInScan](DaqAInScan),[DaqAOutScan](DaqAOutScan).  
  
4/15/05 dgp Wrote it.  
12/18/07  mpr   added second argument and made first optional  
1/11/08   mpr   swept through trying to improve consistency across daq  
                    functions  
5/22/08   mk  Add (untested!) support for USB-1024LS box.   
5/23/08   mk  Add caching for HID device list.   
07/31/16  mk  Remove experimental note about 1024LS. It's tested and known to work.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqDIn.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqDIn.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqDIn.m</code>
</div>

