# [DriftDemo5](DriftDemo5)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

function [DriftDemo5](DriftDemo5)(angle, cyclespersecond, f, drawmask)  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Display animated gratings using the new [Screen](Screen)('DrawTexture') command.  
  
The demo shows two drifting sine gratings through circular apertures. The  
1st drifting grating is surrounded by an annulus (a ring) that shows a  
second drifting grating with a different orientation.  
  
The demo ends after a key press or after 20 seconds have elapsed.  
  
The demo uses alpha-blending and color buffer masking for masking the  
gratings with circular apertures.  
  
### Parameters:  
  
angle = Angle of the grating with respect to the vertical direction.  
cyclespersecond = Speed of grating in cycles per second. f = Frequency of  
grating in cycles per pixel.  
drawmask = If set to 1, then a gaussian aperture is drawn over the grating  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
see also: [PsychDemos](PsychDemos), [MovieDemo](MovieDemo)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/DriftDemo5.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/DriftDemo5.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/DriftDemo5.m</code>
</div>

