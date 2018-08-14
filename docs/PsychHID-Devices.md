# [PsychHID('Devices')](PsychHID-Devices) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction


Return a struct array describing each connected USB HID device.  
'deviceClass' optionally selects for the class of input device. This is not  
supported on all operating systems and will be silently ignored if unsupported.  
On Linux you can select the following classes of input devices: 1 =  
[MasterPointer](MasterPointer), 2 = [MasterKeyboard](MasterKeyboard), 3 = [SlavePointer](SlavePointer) 4 = [SlaveKeyboard](SlaveKeyboard), 5 =  
Floating slave device.  
  
deviceClass -1 returns the numeric deviceIndex of the default keyboard device  
for keyboard queues.  
  
Not all device properties are returned on all operating systems. A zero, empty  
or -1 value for a property in the returned structs can mean that the information  
could not be returned.  
  


###See also:

