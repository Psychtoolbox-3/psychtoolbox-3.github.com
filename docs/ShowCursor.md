# [ShowCursor](ShowCursor)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

oldType = [ShowCursor](ShowCursor)([type][, screenidOrWindow=0][, mouseid])  
  
[ShowCursor](ShowCursor) redisplays the mouse pointer after a previous call to [HideCursor](HideCursor).  
  
If the optional 'type' is specified, it also allows to alter the shape of the  
cursor. Note that this function may not have any effect if the cursor location  
is not on top of an open onscreen window, as cursor visibility or shape may not  
be under Psychtoolbox control while the cursor interacts with other desktop  
items.  
  
'screenidOrWindow' allows to specify the screen or onscreen window to which  
the function should apply. Although optional, it is strongly recommended to  
provide this parameter for cross-platform compatibility across operating systems.  
  
The optional 'mouseid' allows to select which mouse cursor shall be redisplayed  
or changed in visual appearance. This only makes sense if you have multiple  
visible mouse cursors, and it is a Linux/X11 only feature.  
  
The return value 'oldType' is always zero, as this query mechanism is not  
supported with PTB-3. Just returned for backwards-compatibility.  
  
### Cursor shape can be selected. These types are defined by name:  
  
'Arrow' = Standard mouse-pointer arrow.  
'CrossHair' = A cross-hair cursor.  
'Hand' = A hand symbol.  
'SandClock' = Some sort of sand clock/hour-glass (not available on OSX).  
'TextCursor' = A text selection/caret placement cursor (AKA I Beam).  
  
Apart from those names, you can pass integral numbers for 'type' to select  
further shapes. The mapping of numbers to shapes is operating system  
dependent, and therefore not portable across different platforms. On  
MS-Windows, you can select between number 0 to 13. On Linux/X11 you can  
select from a wide range of numbers from 0 up to (at least) 152, maybe  
more, depending on your setup. See the C header file "X11/cursorfont.h"  
for a mapping of numbers to shapes. Passing invalid numbers can create  
errors. On Linux with Wayland backend, you can pass custom additional  
namestrings as 'type'.  
  
LINUX: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Linux allows for display and handling of multiple mouse cursors if your  
X-Server is of version 1.7 or later, or if you use the Wayland display  
backend on a modern Wayland server.  
  
OSX: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
### If provided, an optional numeric 'type' argument changes the cursor shape to:  
  
  0: Arrow  = like 'Arrow'  
  4: I Beam = like 'TextCursor'  
  5: Cross  = like 'CrossHair'  
 10: Hand   = like 'Hand'  
  
Better use the names for cross platform portability!  
  
Windows: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
### If provided, an optional numeric 'type' argument changes the cursor shape to:  
  
  0: Arrow (IDC\_ARROW)  
  1: Crosshair (IDC\_CROSS)  
  2: Hand (IDC\_HAND)  
  3: Four-pointed arrow pointing north, south, east, and west (IDC\_SIZEALL)  
  4: Double-pointed arrow pointing north and south (IDC\_SIZENS)  
  5: Double-pointed arrow pointing west and east (IDC\_SIZEWE)  
  6: Hourglass (IDC\_WAIT)  
  7: Slashed circle (IDC\_NO)  
  8: I-beam (IDC\_IBEAM)  
  9: Double-pointed arrow pointing northeast and southwest (IDC\_SIZENESW)  
 10: Double-pointed arrow pointing northwest and southeast (IDC\_SIZENWSE)  
 11: Standard arrow and small hourglass (IDC\_APPSTARTING)  
 12: Arrow and question mark (IDC\_HELP)  
 13: Vertical arrow (IDC\_UPARROW)  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/ShowCursor.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/ShowCursor.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/ShowCursor.m</code>
</div>

