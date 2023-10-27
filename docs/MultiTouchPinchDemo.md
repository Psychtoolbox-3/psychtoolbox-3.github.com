# [MultiTouchPinchDemo](MultiTouchPinchDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[MultiTouchPinchDemo](MultiTouchPinchDemo)([dev][, screenId=max][, debug=0]) - A basic demo for multi-touch touchscreens.  
  
Run it. Pressing the [ESCape](ESCape) key, or comleting ten demo trials will stop it.  
  
This shows implementation of simple code for "two finger pinch" detection.  
The demo draws a line segment at random location and expects the user to put  
to finger on the touch screen to "squeeze" the line segment between their finger.  
It will complete a trial if both fingers are moved close enough and the line  
segment is between both fingers.  
  
Motivated by the line-intersection task from:  
https://psychtoolbox.discourse.group/t/help-with-multitouch/4953  
  
The demo will try to use the first available touchscreen, or if  
there isn't any touchscreen, the first available touchpad. You  
can also select a specific touch device by passing in its 'dev'  
device handle. Use of touchpads usually needs special configuration.  
See "help [TouchInput](TouchInput)" for more info.  
  
You can select a specific screen to display on - usually the screenId  
of the touch screen display surface - with the optional 'screenId' parameter,  
or it will select the default maximum screenId if omitted.  
  
This demo currently works on Linux + X11 display system, not on Linux + Wayland.  
It also works on MS-Windows 10 and later.  
  
For background info on capabilities and setup see "help [TouchInput](TouchInput)".  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/MultiTouchPinchDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/MultiTouchPinchDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/MultiTouchPinchDemo.m</code>
</div>

