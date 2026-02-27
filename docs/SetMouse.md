# [SetMouse](SetMouse)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[SetMouse](SetMouse)(x, y [, windowPtrOrScreenNumber][, mouseid][, detachFromMouse=0])  
  
Position the mouse cursor on the screen.  
  
The cursor position (x,y) is "local" to the screen, i.e. relative to the  
origin of the screen if a screen number is supplied, or relative to the  
origin of a screen on which a supplied onscreen window is displayed.  
Otherwise it's "global", i.e. relative to the origin of the main screen  
([Screen](Screen) 0). It is advisable to specify an onscreen window handle for  
proper handling of Retina displays on macOS if you use backwards  
compatibility mode. Note: (x,y) is always local to the onscreen window on  
Linux with Wayland, as of the year 2025, a stark difference to all other systems!  
  
On Linux with X11, the optional 'mouseid' parameter allows to select  
which of potentially multiple cursors should be repositioned. On OS/X and  
Windows this parameter is silently ignored.  
  
On macOS, the optional 'detachFromMouse' parameter, if set to 1 instead of  
its default value of zero, will detach mouse cursor movements from mouse  
movements. The cursor will be frozen in place and can only be moved via  
[SetMouse](SetMouse)(), but no longer via mouse movements. On Linux and Windows this  
parameter is currently silently ignored.  
  
On Linux with the Wayland backend, this function is only supported by some  
Wayland based GUI's, but not others. On systems lacking [SetMouse](SetMouse)() support,  
a warning message will be printed. On systems with support, it is up to the  
display server if the [SetMouse](SetMouse)() request is actually honored, or ignored, but  
in general it only works while an onscreen window has pointer focus, and then  
the provided (x,y) position is local to the onscreen window, not to the screen,  
as opposed to how it works on non-Wayland systems! This is sadly unavoidable, due  
to Waylands refusal to operate anything in desktop global coordinates.  
The following link may give some info about which Wayland GUI's support mouse  
cursor positioning: https://wayland.app/protocols/pointer-warp-v1\#wp\_pointer\_warp\_v1  
  
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

