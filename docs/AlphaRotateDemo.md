# [AlphaRotateDemo](AlphaRotateDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[AlphaRotateDemo](AlphaRotateDemo)(numFrames, ifis)  
  
numFrames Number of grating textures to use for the drifting grating...  
  
ifis = Number of monitor refreshes to wait between drawing single  
textures...  
  
  
OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Display a rotating grating using the new [Screen](Screen)('DrawTexture') command.  
In the OS X Psychtoolbox [Screen](Screen)('DrawTexture') replaces  
[Screen](Screen)('CopyWindow').       
  
This illustrates an application of Alpha blending by masking the rotating  
grating with a gaussian transparency mask.  
  
In each frame, first the grating is drawn. Then a texture acting as a  
transparency mask is drawn "over" the grating, masking out selected  
parts of the grating.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
see also: [PsychDemos](PsychDemos), [MovieDemo](MovieDemo)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/AlphaRotateDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/AlphaRotateDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/AlphaRotateDemo.m</code>
</div>

