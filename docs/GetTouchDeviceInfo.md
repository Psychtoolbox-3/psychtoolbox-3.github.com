# [GetTouchDeviceInfo](GetTouchDeviceInfo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

info = [GetTouchDeviceInfo](GetTouchDeviceInfo)(deviceIndex)  
  
Return 'info' a struct with info about the specified touch input device  
'deviceIndex'. 'info' has the following fields:  
  
'product', 'serialNumber' and 'locationID' Self explanatory.  
  
'maxTouchpoints' The maximum number of simultaneously supported touch  
points on the device. 10 is a quite common number for typical touchscreens.  
  
'touchDeviceType': 0 = Touchpad, 1 = Touchscreen.  
  
'valuatorInfos': A struct array. Each slot contains info about the meaning,  
parameter range and resolution of the corresponding value in the Valuators  
vector returned as part of touch events. i'th slot == i'th vector entry.  
This is mostly for use with [GetTouchValuators](GetTouchValuators)() to map raw valuator values  
into something meaningful.  
  
WINDOWS: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
This function currently returns nothing, as touch devices aren't yet  
supported.  
  
OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
This function currently returns nothing, as OSX does not support touch  
screens in a meaningful way as far as we know. And Psychtoolbox for OSX  
currently does not implement any special support for touchpads or such.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
see also: [GetTouchDeviceIndices](GetTouchDeviceIndices), [GetTouchValuators](GetTouchValuators), [TouchEventGet](TouchEventGet)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/GetTouchDeviceInfo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/GetTouchDeviceInfo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/GetTouchDeviceInfo.m</code>
</div>

