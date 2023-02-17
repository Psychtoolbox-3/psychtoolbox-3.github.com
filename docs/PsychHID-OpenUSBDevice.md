# [PsychHID('OpenUSBDevice')](PsychHID-OpenUSBDevice) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction

usbHandle = PsychHID('OpenUSBDevice', vendorID, deviceID [, configurationId=0])

Tries to open and initialize a generic USB device specified by 'vendorID' and  
'deviceID'.  
On success, a 'usbHandle' to the opened device is returned.  
'vendorID' and 'deviceID' must be numeric (integer) values which identify the  
target device by the official vendor id of the device manufacturer, and the  
device id of the specific model of a device.  
'configurationId' optional: Set USB device configuration to given value. By  
default, configuration zero is chosen. Changing the configuration id is only  
possible if the device isn't in use already, and not under control of an  
operating system device driver. A value of -1 would skip changing the  
configuration.  
A call with supported = [PsychHID](PsychHID)('OpenUSBDevice', -1, -1); returns USB low-level  
support status: 1 = Supported, 0 = Not supported, e.g., due to missing libusb-1  
library.  
  


###See also:
[CloseUSBDevice](PsychHID-CloseUSBDevice) [USBControlTransfer](PsychHID-USBControlTransfer) [USBBulkTransfer](PsychHID-USBBulkTransfer) [USBInterruptTransfer](PsychHID-USBInterruptTransfer)
