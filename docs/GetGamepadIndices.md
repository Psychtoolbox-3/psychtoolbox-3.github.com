# [GetGamepadIndices](GetGamepadIndices)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[gamepadIndices, productNames, allInfos] = [GetGamepadIndices](GetGamepadIndices)([productName][, serialNumber][, locationID])  
  
[PsychHID](PsychHID) assigns each USB HID device connected to you computer a  
unique index. [GetGamepadIndices](GetGamepadIndices) returns the indices for those HID devices  
which are gamepads. The product names of each gamepad are returned in a  
second argument which is useful to identify the gamepad associated with  
an index. The third return argument is a cell-array with complete  
information about the gamepad device, e.g., allInfos{1} returns  
all known info about the 1st detected gamepad.  
  
If you have multiple gamepads connected you can restrict the set of  
returned gamepads by specifying the following optional match-critera:  
  
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
               On Linux X11 this is currently remapped to interfaceID,  
               as locationID is not meaningful in the current implementation.  
  
WINDOWS: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
[GetGamepadIndices](GetGamepadIndices) does not work on Windows.  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
see also: [GetKeyboardIndices](GetKeyboardIndices)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/GetGamepadIndices.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/GetGamepadIndices.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/GetGamepadIndices.m</code>
</div>

