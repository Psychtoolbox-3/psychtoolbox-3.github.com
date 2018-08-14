# [FrameSequentialStereoTest](FrameSequentialStereoTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[FrameSequentialStereoTest](FrameSequentialStereoTest)(screenid)  
  
Tests presentation order and timing of stimulus onset in frame sequential  
stereo mode. This is a perceptual test.  
  
The test will run on the screen with the highest number by default, but  
you can pass a 'screenid' to it, if you want.  
  
After startup, the display will show a mostly constant yellow, red or  
green display. Depending on what you see, it tells you how your graphics  
hardware syncs buffer onset:  
  
A) If you see a constant yellow screen, then your hardware always makes sure  
that a full stereo cycle is presented before executing a [Screen](Screen)('flip')  
command, however its not defined if onset of a new stimulus will happen  
with the left buffer first or with the right buffer. You'd need  
measurement equipment to verify which is the startbuffer. The granularity  
of buffer swaps will be reduced to the duration of two video refresh  
intervals, as indicated by the 'ifi' number printed to the Matlab window.  
  
B) If you see either a constant green or a constant red at each run of the  
script (always red or always green, never anything else), then your  
hardware will sync bufferswaps always to the onset of the left stereo  
buffer (if you see red) or to the right buffer (if you see green).  
  
C) If you see either a constant green or a constant red during one run of the  
script, but you observe different colors at repeated runs of the script,  
or a slow switching between red and green, then that means that your  
hardware doesn't care about syncing bufferswaps to a fixed buffer,  
instead it just swaps at the next VBL, so either the left- or the right-  
stereo buffer of a new stimulus will show first. The maximum flip rate is  
equal to the monitor refresh rate.  
  
In case C) you are out of luck if you use Microsoft Windows. If you use  
Linux, then contact the forum with a feature request, we may implement a  
solution for you. If you run [MacOS](MacOS)/X, you can 'force' the graphics  
hardware to always synchronize stimulus onset (flip) to either the left-  
or the right buffers display cycle, and you can query which buffer was  
displayed first after flip, left- or right. However this is a software  
trick which needs calibration. To test if the trick works on your setup,  
do the following:  
  
1. Wait until color of the display settles to either red or green.  
2. If its green, press the 'g' key, if its red, press the 'r' key.  
3. After a short period, the display should settle to a nice green,  
indicating that the trick works, and PTB should write 'GREEN' to the  
Matlab window.  
4. If the display doesn't stabilize to green, but at least the output of  
the Matlab window corresponds with your percept (GREEN for green, RED for  
red) then that means that your system has very noisy timing.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/FrameSequentialStereoTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/FrameSequentialStereoTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/FrameSequentialStereoTest.m</code>
</div>

