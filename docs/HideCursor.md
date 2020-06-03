# [HideCursor](HideCursor)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[HideCursor](HideCursor)([screenidOrWindow=0][, mouseid])  
  
[HideCursor](HideCursor) hides the mouse cursor associated with 'screenidOrWindow'.  
  
'screenidOrWindow' allows to specify the screen or onscreen window to which  
the function should apply.  
  
By default, the cursor on screen zero on Linux/X11, and on all screens on  
Windows and Mac OS/X is hidden. Although optional, it is strongly recommended  
to provide this parameter for cross-platform compatibility across operating  
systems.  
  
Note that this function may not have any effect if the cursor location is not  
on top of an open onscreen window, as cursor visibility or shape may not be  
under Psychtoolbox control while the cursor interacts with other applications  
windows. It may also do nothing if you call the function while no onscreen  
window is open at all. For this reason, you should place calls to [HideCursor](HideCursor)  
after the calls to [Screen](Screen)('OpenWindow') or [PsychImaging](PsychImaging)('OpenWindow'), not  
before them.  
  
'mouseid' defines which of multiple cursors shall be hidden on Linux/X11. The  
parameter is silently ignored on other systems.  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See [ShowCursor](ShowCursor), [SetMouse](SetMouse)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/HideCursor.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/HideCursor.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/HideCursor.m</code>
</div>

