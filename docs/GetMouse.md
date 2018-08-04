# [GetMouse](GetMouse)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[x,y,buttons,focus,valuators,valinfo] = [GetMouse](GetMouse)([windowPtrOrScreenNumber][, mouseDev])  
  
Returns the current (x,y) position of the cursor and the up/down state  
of the mouse buttons. "buttons" is a 1xN matrix where N is the number of  
mouse buttons. Each element of the matrix represents one mouse button.  
The element is true (1) if the corresponding mouse button is pressed and  
false (0) otherwise.  
  
If an optional windowPtr argument for an onscreen window is provided,  
[GetMouse](GetMouse) will also return the window focus state as optional 4th  
return argument 'focus'. 'focus' is 1 if the window has input focus  
and zero otherwise.   
  
The optional 'mouseDev' parameter allows to select a specific mouse or  
pointer device to query if your system has multiple pointer devices.  
Currently Linux only, silently ignored on other operating systems.  
  
On Linux, the optional 'valuator' return argument contains the current  
values of all axis on a multi-axis device, ie., a device which not only  
has an x- and y-axis like a conventional mouse. E.g., digitizer tablets  
(like the "Wacom" pen tablets), may also have axis (also called "valuators")  
which report pen rotation, pen tilt and yaw angle wrt. the tablet surface,  
distance to the tablet surface, or normal and tangential pen pressure.  
Touchpads or trackpads may return contact area with the finger, or pressure.  
Joysticks may return info about additional sliders, wheels or other controls  
beyond the deflection of the joystick itself.  
  
'valuators' is a vector with one double value per axis on Linux. On OSX the  
first two entries will return info about relative mouse movement (deltaX,  
deltaY) since last query, as reported by the OS with unknown reliability in  
unknown units, but probably pixels - use with caution! On MS-Windows, valuator  
is an empty matrix.  
  
The optional 'valinfo' struct array contains one struct per valuator.  
The struct contains fields with info about a valuator, e.g., minimum  
and maximum value, resolution and a label. This is only supported on Linux.  
On other systems it is an empty matrix, except on OSX where it reports  
marginally useful info.  
  
  
% Test if any mouse button is pressed.   
if any(buttons)  
  fprintf('Someone''s pressing a button.\n');  
end  
  
% Test if the first mouse button is pressed.  
if buttons(1)  
  fprintf('Someone''s pressing the first button!\n');  
end  
  
% Test if the second mouse button is pressed.  
if length(buttons)\>=2 && buttons(2)  
  fprintf('Someone''s pressing the second button!\n');  
end  
  
length(buttons) tells you how many buttons there are on your mouse.  
  
The cursor position (x,y) is "local", i.e. relative to the origin of  
the window or screen, if supplied. Otherwise it's "global", i.e. relative  
to the origin of the main screen (the one with the menu bar).  
  
NOTE: If you use [GetMouse](GetMouse) to wait for clicks, don't forget to wait  
for the user to release the mouse button, ending the current click, before  
you begin waiting for the next mouse press.  
  
Alternatively, you can also use the [GetClicks](GetClicks)() function to wait for  
mouse-clicks and return the mouse position of first click and the number  
of mouse button clicks.  
  
fprintf('Please click the mouse now.\n');  
[x,y,buttons] = [GetMouse](GetMouse);  
while any(buttons) % if already down, wait for release  
  [x,y,buttons] = [GetMouse](GetMouse);  
end  
while ~any(buttons) % wait for press  
  [x,y,buttons] = [GetMouse](GetMouse);  
end  
while any(buttons) % wait for release  
  [x,y,buttons] = [GetMouse](GetMouse);  
end  
fprintf('You clicked! Thanks.\n');  
  
NOTE: [GetMouse](GetMouse) no longer supports this obsolete usage:  
xy = [GetMouse](GetMouse)([windowPtrOrScreenNumber])  
where xy is a 1x2 vector containing the x, y coordinates.  
  
OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Even if your mouse has more than three buttons, [GetMouse](GetMouse) will return as  
many values as your mouse has buttons. [GetMouse](GetMouse) can't distinguish between  
multiple mice and will always return the unified state of all mice.  
  
LINUX: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[GetMouse](GetMouse) can distinguish between multiple mouse-like devices. It can return  
information about additional axis (valuators). [GetMouse](GetMouse) not only returns  
status info about mouse/trackpad/trackball devices, but also info about  
Pen digitizer tablets (e.g., Wacom tablets), touch pads and touch screens,  
and joystick/gamepad devices. Usually you'd use the [GamePad](GamePad)() function though  
for Joystick/Gamepad query.  
  
M$-Windows: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
### Limitations:  
  
[GetMouse](GetMouse) will always assume a three button mouse and therefore always  
return the state of three buttons. [GetMouse](GetMouse) can't distinguish between  
multiple mice and will always return the unified state of all mice.  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
See also: [GetClicks](GetClicks), [SetMouse](SetMouse)  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/GetMouse.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/GetMouse.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/GetMouse.m</code>
</div>

