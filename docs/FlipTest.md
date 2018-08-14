# [FlipTest](FlipTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[FlipTest](FlipTest)  
  
[FlipTest](FlipTest) times and plots the intervals between flips of the front and  
back display buffers in a tight loop.  Flips should occur at the video  
frame period.  Result of lipTest are a test of [Priority](Priority)'s ability to  
gurantee time to MATLAB for real-time displays.    
  
On OS X, the [Screen](Screen) subfunction '[Flip](Flip)' replaces 'WaitBlanking' as a means   
of sycnrhonizing updates of video memory with the vertical retrace of your  
monitor.  This prevents vertical shearing of displays.  
  
Onscreen windows in OS X are double buffered, having two surfaces:  
front and back.  The front surface is memory from which video [DACs](DACs) read  
and is displayed on your montitor.  The back surface is video memory to   
which rendering commands draw.  
  
A call to [Screen](Screen) '[Flip](Flip)' delays until the next vertical retrace, then  
instantaneously interchanges front and back video surfaces, and then  
returns.      




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/FlipTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/FlipTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/FlipTest.m</code>
</div>

