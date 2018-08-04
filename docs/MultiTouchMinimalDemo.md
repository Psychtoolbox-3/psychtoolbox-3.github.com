# [MultiTouchMinimalDemo](MultiTouchMinimalDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[MultiTouchMinimalDemo](MultiTouchMinimalDemo)([dev][, verbose=0]) - A basic demo for multi-touch touchscreens.  
  
Run it. Pressing any key will stop it.  
  
Touch the screen and watch the nice colorful happy blobs  
sprinkle to life :)  
  
The demo will try to use the first available touchscreen, or if  
there isn't any touchscreen, the first available touchpad. You  
can also select a specific touch device by passing in its 'dev'  
device handle. Use of touchpads usually needs special configuration.  
See "help [TouchInput](TouchInput)" for more info.  
  
If you set the optional 'verbose' flag to 1, then the unique touch  
id and time delta in msecs between touch updates for each touchpoint  
will be printed. This slows the processing down somewhat, as 'DrawText'  
is more slow than most other drawing functions.  
  
This demo currently only works on Linux + X11 display system,  
not on Linux + Wayland, not on other operating systems.  
  
For background info on capabilities and setup see "help [TouchInput](TouchInput)".  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/MultiTouchMinimalDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/MultiTouchMinimalDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/MultiTouchMinimalDemo.m</code>
</div>

