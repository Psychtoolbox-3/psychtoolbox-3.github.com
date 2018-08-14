# [DaqFunctions](DaqFunctions)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

The Daq Toolbox functions.  
  
\* Analog input/output commands \*  
[DaqAIn](DaqAIn)                  Read analog in  
[DaqAInScan](DaqAInScan)              Scan analog channels  
[DaqAInStop](DaqAInStop)              Stop input scan  
[DaqAInScanBegin](DaqAInScanBegin)         Begin sampling.  
[DaqAInScanContinue](DaqAInScanContinue)      Continue sampling: transfer data from Mac OS to [PsychHID](PsychHID).  
[DaqAInScanEnd](DaqAInScanEnd)           End sampling: data are returned.  
[DaqALoadQueue](DaqALoadQueue)           Set channel gains  
[DaqAOut](DaqAOut)                 Write analog out  
[DaqAOutScan](DaqAOutScan)             Clocked analog out  
[DaqAOutStop](DaqAOutStop)             Stop output scan  
  
\* Digital input/output commands \*  
[DaqDConfigPort](DaqDConfigPort)          Configure digital port  
[DaqDIn](DaqDIn)                  Read digital ports  
[DaqDOut](DaqDOut)                 Write digital port  
[DaqDConfigPortBit](DaqDConfigPortBit)       Configure individual port bits  
[DaqDReadBit](DaqDReadBit)             Read single bit from digital port  
[DaqDWriteBit](DaqDWriteBit)            Write single bit to digital port  
  
\* Miscellaneous commands \*  
[DaqDeviceIndex](DaqDeviceIndex)          Get reference(s) to our device(s)  
[DaqFind](DaqFind)                 Return [DeviceIndex](DeviceIndex) iff one device is connected  
[DaqBlinkLED](DaqBlinkLED)             Cause LED to blink  
[DaqCInit](DaqCInit)                Initialize counter  
[DaqCIn](DaqCIn)                  Read counter  
[DaqGetAll](DaqGetAll)               Retrieve all analog and digital input values  
[DaqGetStatus](DaqGetStatus)            Retrieve device status  
[DaqReset](DaqReset)                Reset the device  
[DaqSetCal](DaqSetCal)               Set CAL output  
[DaqCalibrateAIn](DaqCalibrateAIn)         for 1608 only; measure and store calibration data  
[DaqSetSync](DaqSetSync)              Configure sync  
[DaqSetTrigger](DaqSetTrigger)           Configure ext. trigger  
  
\* Memory commands \*  
[DaqMemRead](DaqMemRead)              Read memory  
[DaqMemWrite](DaqMemWrite)             Write memory  
[DaqReadCode](DaqReadCode)             Read program memory  
[DaqPrepareDownload](DaqPrepareDownload)      Prepare for program memory download  
[DaqWriteCode](DaqWriteCode)            Write program memory  
[DaqWriteSerialNumber](DaqWriteSerialNumber)    Write a new serial number to device  
  
See also Daq, [DaqTest](DaqTest), [DaqPins](DaqPins), [DaqCalls](DaqCalls), [DaqCodes](DaqCodes),  
[DaqDeviceIndex](DaqDeviceIndex), [DaqDIn](DaqDIn), [DaqDOut](DaqDOut), [DaqAIn](DaqAIn), [DaqAOut](DaqAOut), [DaqAInScan](DaqAInScan),[DaqAOutScan](DaqAOutScan).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqFunctions.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqFunctions.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqFunctions.m</code>
</div>

