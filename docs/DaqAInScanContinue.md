# [DaqAInScanContinue](DaqAInScanContinue)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

[params, data] = [DaqAInScanContinue](DaqAInScanContinue)[(DeviceIndex]((DeviceIndex), options [, wantLiveData=0])  
  
Calls [DaqAInScan](DaqAInScan) with the options set to only continue, and not begin or  
end. You may call [DaqAInScanContinue](DaqAInScanContinue) as many times as you like, to keep  
transferring reports from the system to [PsychHID](PsychHID). Eventually you should   
call [DaqAInScanEnd](DaqAInScanEnd) to end aquisition and get all remaining data.  
  
If you want to retrieve already captured data, set the optional  
'wantLiveData' flag to 1. This will return all already received data in  
the optional return argument 'data', in the same format as [DaqAInScanEnd](DaqAInScanEnd)  
would provide.  
  
See also [DaqAInScan](DaqAInScan), [DaqAInScanBegin](DaqAInScanBegin), [DaqAInScanEnd](DaqAInScanEnd),  
Daq, [DaqPins](DaqPins), [DaqTest](DaqTest), [PsychHIDTest](PsychHIDTest).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqAInScanContinue.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqAInScanContinue.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqAInScanContinue.m</code>
</div>

