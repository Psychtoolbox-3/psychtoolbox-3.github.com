# [GetMouseIndices](GetMouseIndices)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[mouseIndices, productNames, allInfo] = [GetMouseIndices](GetMouseIndices)([typeOnly][, productName][, serialNumber][, locationID])  
  
OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[PsychHID](PsychHID) assigns each USB HID device connected to you computer a unique  
index. [GetMouseIndices](GetMouseIndices) returns the indices for those HID devices which  
are mouses. The product names of the mouses are returned in a second  
argument which is useful to identify the mouse associated with a  
paticular index. For complete information on a gamepad use  
[PsychHID](PsychHID)('Devices').  
  
LINUX: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[GetMouseIndices](GetMouseIndices) allows selection of different types of pointing devices  
via the optional 'typeOnly' argument:  
'masterPointer' will only return indices of so called "master pointer"  
devices. These correspond to visible mouse cursors. 'slavePointer' will  
only return indices of slave pointer devices. If you want to use keyboard  
query functions like [KbCheck](KbCheck), [KbWait](KbWait) etc. to get mouse button presses,  
then you can only use slave pointer devices, ie., select between mice that  
are returned by setting 'typeOnly' as 'slavePointer'.  
  
WINDOWS: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[GetMouseIndices](GetMouseIndices) can not enumerate individual mice. All connected pointing  
devices are treated as one unified mouse.  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
If you have multiple mice connected you can restrict the set of  
returned mouse by specifying the following optional match-critera:  
  
product      = Product name of target devices, as returned in 'productNames'.  
  
serialNumber = Serial number of target devices. This is a text string,  
               not a number!  
  
locationID   = Numeric id of where the device is connected to the  
               computer. The number is supposed to be unique for a given  
               connection port. E.g., the same number will be returned  
               whenever the device is connected to the same USB port of  
               the computer. The value should be persistent across  
               reboots of the machine, but may not be persistent across  
               operating system upgrades - or may not be persistent at  
               all in case of os bugs. Your mileage may vary...  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
see also: [GetKeyboardIndices](GetKeyboardIndices), [GetKeypadIndices](GetKeypadIndices), [GetGamepadIndices](GetGamepadIndices)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/GetMouseIndices.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/GetMouseIndices.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/GetMouseIndices.m</code>
</div>

