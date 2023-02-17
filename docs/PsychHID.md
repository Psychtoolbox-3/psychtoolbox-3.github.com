# [PsychHID](PsychHID)
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID)

Usage:  
  
  
General commands:  
  
  
rc = PsychHID('[KeyboardHelper](PsychHID-KeyboardHelper)', commandCode)  
  
  
Support for generic USB-HID devices:  
  
  
numberOfDevices=PsychHID('[NumDevices](PsychHID-NumDevices)')  
devices=PsychHID('[Devices](PsychHID-Devices)' [, deviceClass])  
elementState=PsychHID('[RawState](PsychHID-RawState)',deviceNumber,elementNumber)  
[keyIsDown,secs,keyCode]=PsychHID('[KbCheck](PsychHID-KbCheck)' [, deviceNumber][, scanList])  
[report,err]=PsychHID('[GetReport](PsychHID-GetReport)',deviceNumber,reportType,reportID,reportBytes)  
err=PsychHID('[SetReport](PsychHID-SetReport)',deviceNumber,reportType,reportID,report)  
[reports,err]=PsychHID('[GiveMeReports](PsychHID-GiveMeReports)',deviceNumber,[reportBytes])  
err=PsychHID('[ReceiveReports](PsychHID-ReceiveReports)',deviceNumber[,options])  
err=PsychHID('[ReceiveReportsStop](PsychHID-ReceiveReportsStop)',deviceNumber)  
  
  
Queue based keyboard queries: See 'help KbQueueCreate' for explanations:  
  
  
PsychHID('[KbQueueCreate](PsychHID-KbQueueCreate)', [deviceNumber][, keyFlags=all][, numValuators=0][, numSlots=10000][, flags=0][, windowHandle=0])  
PsychHID('[KbQueueRelease](PsychHID-KbQueueRelease)' [, deviceIndex])  
[navail] = PsychHID('[KbQueueFlush](PsychHID-KbQueueFlush)' [, deviceIndex][, flushType=1])  
PsychHID('[KbQueueStart](PsychHID-KbQueueStart)' [, deviceIndex])  
PsychHID('[KbQueueStop](PsychHID-KbQueueStop)' [, deviceIndex])  
[keyIsDown, firstKeyPressTimes, firstKeyReleaseTimes, lastKeyPressTimes, lastKeyReleaseTimes]=PsychHID('[KbQueueCheck](PsychHID-KbQueueCheck)' [, deviceIndex])  
secs=PsychHID('[KbTriggerWait](PsychHID-KbTriggerWait)', KeysUsage, [deviceNumber])  
[event, navail] = PsychHID('[KbQueueGetEvent](PsychHID-KbQueueGetEvent)' [, deviceIndex][, maxWaitTimeSecs=0])  
  
  
Support for access to generic USB devices: See 'help ColorCal2' for one usage example:  
  
  
usbHandle = PsychHID('[OpenUSBDevice](PsychHID-OpenUSBDevice)', vendorID, deviceID [, configurationId=0])  
PsychHID('[CloseUSBDevice](PsychHID-CloseUSBDevice)' [, usbHandle])  
PsychHID('[USBClaimInterface](PsychHID-USBClaimInterface)', usbHandle, interfaceId)  
[recData, count] = PsychHID('[USBControlTransfer](PsychHID-USBControlTransfer)', usbHandle, bmRequestType, bRequest, wValue, wIndex, wLength [, outData][, timeOutMSecs=10000])  
[countOrRecData] = PsychHID('[USBBulkTransfer](PsychHID-USBBulkTransfer)', usbHandle, endPoint, length [, outData][, timeOutMSecs=10000])  
[countOrRecData] = PsychHID('[USBInterruptTransfer](PsychHID-USBInterruptTransfer)', usbHandle, endPoint, length [, outData][, timeOutMSecs=10000])  
  

ok<STOUT\>  
  


