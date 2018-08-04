# [GetKeyboardIndices](GetKeyboardIndices)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[keyboardIndices, productNames, allInfos] = [GetKeyboardIndices](GetKeyboardIndices)([productName][, serialNumber][, locationID])  
  
The [PsychHID](PsychHID) assigns each USB HID device connected to you computer a  
unique index. [GetKeyboardIndices](GetKeyboardIndices) returns the indices for those HID  
devices which are keyboards.  The product names of each keyboard are  
returned in a second argument which is useful to identify the keyboard  
associated with an index. The third return argument is a cell-array with  
complete information about the keyboard device, e.g., allInfos{1} returns  
all known info about the 1st detected keyboard.  
  
If you have multiple keyboards connected you can restrict the set of  
returned keyboard by specifying the following optional match-critera:  
  
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
WINDOWS: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[GetKeyboardIndices](GetKeyboardIndices) can not enumerate individual keyboards. All keyboard  
devices are treated as one unified keyboard.  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
see also: [GetGamepadIndices](GetGamepadIndices)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/GetKeyboardIndices.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/GetKeyboardIndices.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/GetKeyboardIndices.m</code>
</div>

