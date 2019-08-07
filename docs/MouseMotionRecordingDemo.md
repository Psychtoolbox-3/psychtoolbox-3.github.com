# [MouseMotionRecordingDemo](MouseMotionRecordingDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[MouseMotionRecordingDemo](MouseMotionRecordingDemo) - Record mouse motion via [KbQueues](KbQueues).  
  
This demo shows very basic recording of mouse/touchpad motion  
movement data under Linux and Windows.  
  
Press a key on the keyboard to end the demo.  
  
It requests recording of raw motion, ie. of the device itself,  
in device and operating system specific distance units, not  
neccessarily in screen pixels. No pointe acceleration / ballistics  
should be applied to the motion. It prints cursor position, vs.  
integrated raw position, vs. reported raw movement deltas for  
comparison. Also mouse wheel motion on some OS + device combos.  
  
Note that you may have to calibrate / map reported positions yourself  
for any given mouse device, e.g., a 400 DPI mouse may report in different  
units than a 1000 DPI mouse etc.  
  
This functionality is not supported on Apple macOS.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/MouseMotionRecordingDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/MouseMotionRecordingDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/MouseMotionRecordingDemo.m</code>
</div>

