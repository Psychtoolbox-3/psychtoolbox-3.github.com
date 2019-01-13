# [PsychHID('KbTriggerWait')](PsychHID-KbTriggerWait) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction


Scan a keyboard, keypad, or other HID device with buttons, and wait for a  
trigger key press.  
NOTE: This function should not be called directly! Use [KbTriggerWait](KbTriggerWait)() instead.  
By default the first keyboard device (the one with the lowest device number) is  
scanned. If no keyboard is found, the first keypad device is scanned, followed  
by other devices, e.g., mice.  Optionally, the deviceNumber of any keyboard or  
HID device may be specified.  
The 'KeysUsage' parameter must specify the keycode of a single key to wait for  
on OS/X. On Linux and Windows, 'KeysUsage' can be a vector of trigger key codes  
and the wait will finish as soon as at least one of the keys in the vector is  
pressed.  
On MS-Windows XP and later, it is currently not possible to enumerate different  
keyboards and mice separately. Therefore the 'deviceNumber' argument is mostly  
useless for keyboards and mice, usually you can only check the system keyboard  
or mouse.  
OSX: This function is unsupported. You must use [KbTriggerWait](KbTriggerWait)() instead.  
  


###See also:

