# [DriftWaitDemo](DriftWaitDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[DriftWaitDemo](DriftWaitDemo)([movieDurationSecs=10][, waitframes=1])  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Display an animated grating using the new [Screen](Screen)('DrawTexture') command.  
In Psychtoolbox-3 [Screen](Screen)('DrawTexture') replaces [Screen](Screen)('CopyWindow').  
  
This demo illustrates on how to emulate the old [Screen](Screen)('WaitBlanking'...)  
behaviour: If you set waitframes \> 1 then the screen is only updated  
every waitframes'th monitor refresh interval.  
  
### Optional parameters:  
  
movieDurationSecs == Requested total duration of movie in seconds.  
waitframes == Number of monitor refresh intervals to wait before each  
frame is drawn.  
  
### [CopyWindow](CopyWindow) vs. [DrawTexture](DrawTexture):  
  
In the OS 9 Psychtoolbox, [Screen](Screen) ('CopyWindow") was used for all  
time-critical display of images, in particular for display of the movie  
frames in animated stimuli. In contrast, [Screen](Screen)('DrawTexture') should not  
be used for display of all graphic elements,  but only for  display of  
MATLAB matrices.  For all other graphical elements, such as lines,  rectangles,  
and ovals we recommend that these be drawn directly to the  display  
window during the animation rather than rendered to offscreen  windows  
prior to the animation.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
see also: [PsychDemos](PsychDemos), [MovieDemo](MovieDemo), [DriftDemo](DriftDemo)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/DriftWaitDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/DriftWaitDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/DriftWaitDemo.m</code>
</div>

