# [PsychHID('OpenUSBDevice')](PsychHID-OpenUSBDevice) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction


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
  


###See also:

