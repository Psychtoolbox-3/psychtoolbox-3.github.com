# [Screen('ConstrainCursor')](Screen-ConstrainCursor) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Confine mouse cursor position to a specified area inside onscreen window  
'windowIndex'.  
  
If you set 'addConstraint' to 1, then a region constraint is added: 'rect'  
specifies the rectangle (in window local coordinates) to which the mouse cursor  
should be confined. If you omit 'rect', then the cursor is confined to the  
region of the window, ie. can't leave the window. On MS-Windows you can only  
define one single rectangular region at all, regardless of the number of  
onscreen windows. On Linux/X11 you can define up to a total of (currently) 1024  
confinement regions, e.g., for multiple separate windows, or multiple regions  
per window.  
Additionally on Linux/X11 you can define empty 'rect's which define a horizontal  
or vertical line. This adds a horizontal or vertical border line which can not  
be crossed by the mouse cursor, so you could, e.g., build a complex maze, in  
which the cursor has to navigate. Please note that this ability will not be  
present on a future version of Psychtoolbox for Linux with the Wayland display  
server. While the Wayland implementation will provide the ability to define  
multiple regions, its semantic will very likely be different, so if you use this  
special Linux/X11 only feature, your code will not only be non-portable to  
MS-Windows, but also to future Linux versions which use Wayland instead of the  
X11 graphics system!  
  
If you set 'addConstraint' to 0 and specify a 'rect', then the specified 'rect'  
confinement region for the given onscreen window is removed on Linux/X11. If you  
omit 'rect' on Linux, then all confinement regions for the given onscreen window  
are removed. On MS-Windows the single globally available confinement region is  
removed if it was set for the given onscreen window, regardless if you specify  
'rect' or not, as there is no ambiguity or choice with only one global rect  
anyway.  
  
Closing an onscreen window with active cursor constraints will automatically  
remove all associated cursor confinement regions. This is true for proper close  
via [Screen](Screen)('[Close](Close)', windowIndex), [Screen](Screen)('Closeall') or [sca](sca), or during a  
controlled error abort with proper error handling. On Linux, quitting/killing or  
crashing Octave/Matlab will also release pointer confinement. On MS-Windows,  
pressing ALT+TAB will release the confinement.  
  
The 'ConstrainCursor' function is not currently supported or supportable on  
Apple macOS due to macOS operating system limitations. See 'help SetMouse'  
sections referring to the 'detachFromMouse' parameter for a hint on how you may  
be able to work around this macOS limitation for some applications.  
  
  


###See also:
[HideCursorHelper](Screen-HideCursorHelper)
