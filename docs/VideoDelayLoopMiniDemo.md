# [VideoDelayLoopMiniDemo](VideoDelayLoopMiniDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[VideoDelayLoopMiniDemo](VideoDelayLoopMiniDemo)([delayframes = 0][, duration = 30][, roi][, firewireBasler = 0]);  
  
Demonstrates most simplistic use of [PsychVideoDelayLoop](PsychVideoDelayLoop)() function for  
delayed visual feedback via a camera + display combo.  
  
'delayframes' == Requested delay in captured frames: 0 = Minimal delay  
(i.e. request zero delay, get whatever the minimum of your camera +  
display combo is).  
  
The demo takes some startup time to calibrate, then provides visual  
feedback for 30 seconds, then ends, unless you specifiy a different  
'duration' in seconds.  
  
'firewireBasler' defaults to zero. If set to 1, customize to a Basler  
A602f IIDC-1394 compliant Firewire camera.  
  
Tested on [MacOS](MacOS)/X Intel [MacBookPro](MacBookPro) with builtin iSight camera. However,  
the routine was originally developed, tested and optimized for GNU/Linux,  
so it only provides limited functionality, flexibility and performance on  
other operating systems. The inherent delay of USB cameras like Apples  
builtin iSight is pretty high, so they are not seriously useful for low  
delay feedback. Pick a good IIDC Firewire camera if you want low  
latencies. Use Linux if you want really low latencies and optimal  
control.  
  
This demo is only a proof of concept. Use with caution!  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/VideoDelayLoopMiniDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/VideoDelayLoopMiniDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/VideoDelayLoopMiniDemo.m</code>
</div>

