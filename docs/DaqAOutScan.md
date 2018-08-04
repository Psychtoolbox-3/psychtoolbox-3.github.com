# [DaqAOutScan](DaqAOutScan)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

params=[DaqAOutScan](DaqAOutScan)[(DeviceIndex]((DeviceIndex),v,options)  
USB-1208FS: Analog output scan. Produce sampled analog output voltage  
waveforms on one or two channels. This command sends the values in "v"  
(one column per channel) to the specified range of (one or two) output  
channels.  
  
"params.fActual" is the actual sampling frequency, sample/channel/s.  
      It is as close as possible to the requested sampling frequency  
      options.f.  
"params.countActual" is the actual total sample/channel sent.  
"params.start" is when the first report ("v" data) was sent to the device.  
"params.end" is when the final report was sent to device.  
"[DeviceIndex](DeviceIndex)" is a small integer, the array index specifying which HID  
      device in the array returned by [PsychHID](PsychHID)('Devices') is interface 0   
      of the desired USB-1208FS box.   
"v" is a matrix, with one column per channel. (If you're using only one    
      channel, then you're allowed to send the vector as either a column  
      or a row.) Each value is a double, in the range 0 to 1, which will  
      produce an output voltage in the range 0 to 4.095 V.  
"options.[FirstChannel](FirstChannel)" is the first channel of the scan (0 - 1). (formerly  
      "options.lowChannel" -- that terminology is deprecated.)  
"options.[LastChannel](LastChannel)" is the last channel of the scan (0 - 1), and must   
      be greater than or equal to options.[FirstChannel](FirstChannel). The values  
      options.[FirstChannel](FirstChannel) and options.[LastChannel](LastChannel) specify the channel  
      range for the scan. (Formerly "options.highChannel" -- that terminology  
      is deprecated.)  
"options.f" is the desired sampling frequency, sample/channel/s, in the  
      range 0.596/c to 10e6/c Hz, where c is the number of channels to be  
      scanned.  
"options.trigger" is 1 = use external trigger. The external trigger   
      may be used to start the scan synchronously. If the bit is set, the  
      device will wait until the appropriate trigger edge is detected,  
      then begin emitting samples at the specified rate.   
"options.getReports" is 1 (default) = wait to receive report from  
      USB-1208FS before sending each block of data in "v". 0 = send  
      blocks of data at what should be the right rate.  
"options.print" is 1 = enable diagnostic printing; 0 (default) no   
      diagnostics.  
  
LIMITATIONS: As of 17 April 2005, [DaqAoutScan](DaqAoutScan) works fine at up to 2000  
sample/s with one channel, or up to 200 sample/channel/s with two  
channels. (It is surprising that these two limits are not exactly a  
factor of 2 apart.) When I try to go faster than that I encounter various  
problems. Sometimes I get "data underrun" errors and sometimes the  
[PsychHID](PsychHID) [SetReport](SetReport) call hangs up forever, never returning, making it  
necessary to quit MATLAB. I don't understand why these things happen;  
they shouldn't. I am trying to get help from Measurement Computing and  
Apple to understand and overcome this problems. However, in the meantime,  
the attained rates are enough for my immediate needs, and hopefully that  
will be true for many other users.   
  
See also Daq, [DaqFunctions](DaqFunctions), [DaqPins](DaqPins), [DaqTest](DaqTest), [PsychHIDTest](PsychHIDTest),  
[DaqDeviceIndex](DaqDeviceIndex), [DaqDIn](DaqDIn), [DaqDOut](DaqDOut), [DaqAIn](DaqAIn), [DaqAOut](DaqAOut), [DaqAInScan](DaqAInScan).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqAOutScan.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqAOutScan.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqAOutScan.m</code>
</div>

