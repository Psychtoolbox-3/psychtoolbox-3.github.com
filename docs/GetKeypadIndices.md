# [GetKeypadIndices](GetKeypadIndices)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[keypadIndices, productNames, allInfos] = [GetKeypadIndices](GetKeypadIndices)([productName][, serialNumber][, locationID])  
  
The [PsychHID](PsychHID) assigns each USB HID device connected to you computer a  
unique index. [GetKeypadIndices](GetKeypadIndices) returns the indices for those HID  
devices which are keypads. The product names of each keypad are  
returned in a second argument which is useful to identify the keypad  
associated with an index. The third return argument is a cell-array with  
complete information about the keypad device, e.g., allInfos{1} returns  
all known info about the 1st detected keypad.  
  
If you have multiple keypads connected you can restrict the set of  
returned keypads by specifying the following optional match-critera:  
  
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
WINDOWS: All keypads are treated as one keypad, you can not select between  
different keypads.  
  
see also: [GetGamepadIndices](GetGamepadIndices), [GetKeyBoardIndices](GetKeyBoardIndices)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/GetKeypadIndices.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/GetKeypadIndices.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/GetKeypadIndices.m</code>
</div>

