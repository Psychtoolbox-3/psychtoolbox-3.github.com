# [DaqAInScanBegin](DaqAInScanBegin)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

params=[DaqAInScanBegin](DaqAInScanBegin)[(DeviceIndex]((DeviceIndex),options)  
Calls [DaqAInScan](DaqAInScan) with the options set to only begin, and not continue or  
end. You should subsequently call [DaqAInScanContinue](DaqAInScanContinue) (as many times as  
you like) and, finally, [DaqAInScanEnd](DaqAInScanEnd) to get the data. For example:  
    options.[FirstChannel](FirstChannel)=[FirstChannel](FirstChannel);  
    options.[LastChannel](LastChannel)=[LastChannel](LastChannel);  
    options.count=count;  
    options.f=f;  
    params=[DaqAInScanBegin](DaqAInScanBegin)[(DeviceIndex]((DeviceIndex),options);  
    for i=1:frames  
        % add code here doing something useful  
        params=[DaqAInScanContinue](DaqAInScanContinue)[(DeviceIndex]((DeviceIndex),options);  
    end  
    params=[DaqAInScanContinue](DaqAInScanContinue)[(DeviceIndex]((DeviceIndex),options);  
    [data,params]=[DaqAInScanEnd](DaqAInScanEnd)[(DeviceIndex]((DeviceIndex),options);  
See also [DaqAInScan](DaqAInScan), [DaqAInScanContinue](DaqAInScanContinue), [DaqAInScanEnd](DaqAInScanEnd),  
Daq, [DaqPins](DaqPins), [DaqTest](DaqTest), [PsychHIDTest](PsychHIDTest).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqAInScanBegin.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqAInScanBegin.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqAInScanBegin.m</code>
</div>

