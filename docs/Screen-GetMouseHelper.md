# [Screen('GetMouseHelper')](Screen-GetMouseHelper) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[x, y, buttonValueArray, hasKbFocus, valuators, valuatorNames]= Screen('GetMouseHelper', numButtons [, screenNumber][, mouseIndex]);

This is a helper function called by [GetMouse](GetMouse).  Do not call  
[Screen](Screen)('GetMouseHelper'), use [GetMouse](GetMouse) instead.  
"numButtons" is the number of mouse buttons to return in buttonValueArray. 1 <=  
numButtons <= 32. Ignored on Linux and Windows.  
"screenNumber" is the number of the PTB screen whose mouse should be queried on  
setups with multiple connected mice. This value is optional (defaults to zero)  
and only honored on GNU/Linux. It's meaningless on OS-X or Windows.  
Well, not quite. If you pass in an onscreen window handle instead of a  
screenNumber, then the 4th optional return argument "hsKbFocus" will return 1 if  
the given onscreen window has keyboard input focus, 0 otherwise.  
"mouseIndex" is the optional index of the (mouse)pointer device. Defaults to  
system pointer. Only honored on Linux.  
"valuators" If the input device has more than two axis (x and y position), e.g.,  
in the case of a touch input device or digitizer tablet, this will be a vector  
of double values, returning the values of those axis. Return values could be,  
e.g., distance to surface, pen pressure, touch area, or pen orientation on a pen  
input device or touchscreen.  
On Windows the first two valuators currently return physical mouse cursor  
position [PhysicalX](PhysicalX) and [PhysicalY](PhysicalY).  
On OSX the first two valuators currently return relative mouse delta movement  
deltaX and deltaY.  
  


###See also:

