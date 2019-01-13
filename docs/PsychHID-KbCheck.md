# [PsychHID('KbCheck')](PsychHID-KbCheck) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction


Scan a keyboard, keypad, or other HID device with buttons, and return a vector  
of logical values indicating the state of each key.  
By default the default keyboard device (as determined by some operating system  
dependent heuristic) is scanned. If no keyboard is found, the first keypad  
device is scanned, followed by other devices, e.g., mice. Optionally, the  
'deviceNumber' of any keyboard or HID device may be specified.  
As checking all potentially 256 keys on a HID device is a time consuming  
process, which can easily take up to 1 msec on modern hardware, you can restrict  
the scan to a subset of the 256 keys by providing the optional 'scanList'  
parameter: 'scanList' must be a vector of 256 doubles, where the i'th element  
corresponds to the i'th key and a zero value means: Ignore this key during scan,  
whereas a positive non-zero value means: Scan this key.  
The [PsychHID](PsychHID)('KbCheck') implements the [KbCheck](KbCheck) command as provided by the  OS 9  
Psychtoolbox. [KbCheck](KbCheck) is defined in Psychtoolbox-3 and invokes  
[PsychHID](PsychHID)('KbCheck'). Always use [KbCheck](KbCheck) instead of directly calling  
[PsychHID](PsychHID)('KbCheck'), unless you have very good reasons to do otherwise and  
really know what you're doing!  


###See also:

