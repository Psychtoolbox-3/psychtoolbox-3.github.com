# [kPsychGUIWindow](kPsychGUIWindow)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

kPsychGUIWindow -- Create onscreen windows with behaviour of normal GUI windows.  
  
This flag can be passed to the optional 'specialFlags' parameter of  
[Screen](Screen)('OpenWindow', ...) or [PsychImaging](PsychImaging)('OpenWindow', ...).  
  
It will cause the onscreen window to be a "regular" window that mostly  
behaves like typical GUI windows on your system. The window will have a  
titlebar and title, a border and other decorations. It will have buttons  
and handles to allow it to be moved around, resized, minimized or  
maximized, hidden and so on. Functions like [Screen](Screen)('Rect'),  
[Screen](Screen)('GlobalRect') and [Screen](Screen)('WindowSize') will report the true size  
and position of the window after it has been resized or moved around. The  
[GetMouse](GetMouse)() function will optionally report if the window has keyboard  
input focus because it is the active foreground window.  
  
Window stacking order, transparency and other window manager interactions  
should mostly behave as with other application windows.  
  
Please note that timing precision and timestamp precision for visual  
stimulus onset for this mode will not be guaranteed. Performance may be  
reduced. Other limitations may apply.  
  
GUI window mode is a "best effort" behaviour, as Psychtoolbox is not  
really designed to be - or exactly behave - like a regular GUI toolkit.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/kPsychGUIWindow.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/kPsychGUIWindow.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/kPsychGUIWindow.m</code>
</div>

