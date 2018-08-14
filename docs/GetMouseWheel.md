# [GetMouseWheel](GetMouseWheel)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

wheelDelta = [GetMouseWheel](GetMouseWheel)([mouseIndex])  
  
Return change of mouse wheel position of a wheel mouse (in "wheel clicks")  
since last query. 'mouseIndex' is the device index of the wheel mouse to  
query. The argument is optional: If left out, the first detected real wheel  
mouse is queried.  
  
OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Uses [PsychHID](PsychHID) for low-level access to mice with mouse wheels. If wheel  
state is not queried frequent enough, the internal queue may overflow and  
some mouse wheel movements may get lost, resulting in a smaller reported  
'wheelDelta' than the real delta since last query. On OS X 10.4.11 the  
operating system can store at most 10 discrete wheel movements before it  
discards movement events. This uses low-level code which may not work on  
all wheel mice.  
  
Linux: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Uses [GetMouse](GetMouse)() extra valuators to check if one of the valuators represents  
a mouse wheel, then translates the valuators absolute wheel position into  
wheel delta by keeping track of old values.  
  
MS-Windows: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
This function is not supported and will fail with an error.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
See also: [GetClicks](GetClicks), [GetMouseIndices](GetMouseIndices), [GetMouse](GetMouse), [SetMouse](SetMouse), [ShowCursor](ShowCursor),  
[HideCursor](HideCursor)  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/GetMouseWheel.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/GetMouseWheel.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/GetMouseWheel.m</code>
</div>

