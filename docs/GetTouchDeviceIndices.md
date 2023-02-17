# [GetTouchDeviceIndices](GetTouchDeviceIndices)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[touchIndices, productNames, allInfo] = [GetTouchDeviceIndices](GetTouchDeviceIndices)([typeOnly][, touchTypeOnly][, productName][, serialNumber][, locationID])  
  
Return 'touchIndices' a set of handles to select touch input devices  
like touchscreens, tablets and touchpads for touch input with the  
[TouchXXX](TouchXXX) functions [(TouchQueueCreate]((TouchQueueCreate), [TouchEventGet](TouchEventGet) etc.).  
  
Also returns corresponding productNames for the devices and detailed  
info in the allInfo struct-array.  
  
LINUX: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[GetTouchDeviceIndices](GetTouchDeviceIndices) allows selection of different types of touch devices  
via the optional 'typeOnly' argument:  
'masterPointer' will only return indices of so called "master pointer"  
devices. These correspond to visible mouse cursors. 'slavePointer' will  
only return indices of slave pointer devices. Often only 'slavePointer'  
devices work properly or with full functionality for touch devices, that's  
why typeOnly defaults to 'slavePointer' if the argument is omitted.  
  
Windows: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Basic device enumeration should work, but only true touchscreens are supported,  
not touchpads.  
  
OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
This function currently returns nothing, as OSX does not support touch  
screens in a meaningful way as far as we know. And Psychtoolbox for OSX  
currently does not implement any special support for touchpads or such.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
If you have touch devices connected you can restrict the set of  
returned devices by specifying the following optional match-critera:  
  
typeOnly      = 'masterPointer' or 'slavePointer' or 'allPointers'. If left  
                out, this will default to 'slavePointer', unless on MS-Windows,  
                where it defaults to 'masterPointer'.  
  
touchTypeOnly = 0 for touchpads, 1 for true touchscreens.  
  
product       = Product name of target devices, as returned in 'productNames'.  
  
serialNumber  = Serial number of target devices. This is a text string,  
                not a number!  
  
locationID    = Numeric id of where the device is connected to the  
                computer. The number is supposed to be unique for a given  
                connection port. E.g., the same number will be returned  
                whenever the device is connected to the same USB port of  
                the computer. The value should be persistent across  
                reboots of the machine, but may not be persistent across  
                operating system upgrades - or may not be persistent at  
                all in case of os bugs. Your mileage may vary...  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
see also: [GetKeyboardIndices](GetKeyboardIndices), [GetKeypadIndices](GetKeypadIndices), [GetGamepadIndices](GetGamepadIndices), [GetMouseIndices](GetMouseIndices)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/GetTouchDeviceIndices.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/GetTouchDeviceIndices.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/GetTouchDeviceIndices.m</code>
</div>

