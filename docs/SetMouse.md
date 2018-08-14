# [SetMouse](SetMouse)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[SetMouse](SetMouse)(x, y [, windowPtrOrScreenNumber][, mouseid][, detachFromMouse=0])  
  
Position the mouse cursor on the screen.  
  
The cursor position (x,y) is "local" to the screen, i.e. relative to the  
origin of the screen if a screen number is supplied, or relative to the  
origin of a screen on which a supplied onscreen window is displayed.  
Otherwise it's "global", i.e. relative to the origin of the main screen  
([Screen](Screen) 0).  
  
On Linux with X11, the optional 'mouseid' parameter allows to select  
which of potentially multiple cursors should be repositioned. On OS/X and  
Windows this parameter is silently ignored.  
  
On OSX, the optional 'detachFromMouse' parameter, if set to 1 instead of  
its default value of zero, will detach mouse cursor movements from mouse  
movements. The cursor will be frozen in place and can only be moved via  
[SetMouse](SetMouse)(), but no longer via mouse movements. On Linux and Windows this  
parameter is currently silently ignored.  
  
On Linux with the Wayland backend, this function does nothing.  
  
The delay between a call to [SetMouse](SetMouse) and when [GetMouse](GetMouse) will report the  
new mouse cursor position is not known. [GetMouse](GetMouse) seems to report the new  
position immediately, but we have no guarantee that it always will.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See Also: [GetMouse](GetMouse), [GetClicks](GetClicks)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/SetMouse.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/SetMouse.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/SetMouse.m</code>
</div>

