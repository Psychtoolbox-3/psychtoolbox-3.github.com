# [MovingLineDemo](MovingLineDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[MovingLineDemo](MovingLineDemo)([xv=10][, twolines=0][, screenid=max])  
  
Shows a pair of vertical lines, or a single line, which travel  
horizontally across the display from the left to the right, repeating  
infinitely.  
  
The optional parameter 'xv' defines the speed in pixels per redraw cycle.  
It defaults to 10 pixels per redraw cycle.  
  
The optional parameter 'twolines' selects if one line or a pair of lines  
should be drawn. By default, twolines==0, ie., a single line is drawn.  
  
The optional parameter 'screenid' selects the display screen to use for  
display, it defaults to the secondary display on multi-display setups.  
  
Hold down the right mouse button to pause the animation. Press the left  
mouse button to exit the demo.  
  
The lines show a greyscale gradient, starting with black at the top of  
the screen, ending in white at the bottom. They are seperated by 'xv'  
pixels.  
  
The purpose of this simple animation is to demonstrate differences in the  
way CRT monitors and TFT flat panel display devices display moving  
stimuli. It shows artifacts that are due to both the display technology  
and due to perceptual effects in the visual system.  
  
On a well working CRT monitor, which is an impulse-type display with fast  
response time, you should see a sharp and clearly separated moving pair  
of lines. On a LCD display with its high latency response behaviour and  
its working principle as a hold-type display, you should see a  
significant "smear" or "blur" of the line pair -- or maybe not even a  
pair of distinctive lines anymore. This is due to technical limitations  
of the display technology and due to the "bad" interaction between  
hold-type displays and smooth pursuit eye movements caused by tracking of  
certain types of moving stimuli.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/MovingLineDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/MovingLineDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/MovingLineDemo.m</code>
</div>

