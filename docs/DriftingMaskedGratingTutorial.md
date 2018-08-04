# [DriftingMaskedGratingTutorial](DriftingMaskedGratingTutorial)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[PsychTutorials](PsychTutorials)

function [DriftDemo2](DriftDemo2)(angle, cyclespersecond, f, drawmask)  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Display an animated grating using the new [Screen](Screen)('DrawTexture') command.  
In the OS X Psychtoolbox [Screen](Screen)('DrawTexture') replaces  
[Screen](Screen)('CopyWindow'). The demo will stop after roughly 20 seconds have  
passed or after the user hits a key.  
  
This demo illustrates how to draw an animated grating online by use of  
only one grating texture. We create one texture with a static sine  
grating. In each successive frame we only draw a rectangular subregion of  
the sine-texture onto the screen, basically showing the texture through  
an aperture. The subregion - and therefore our "aperture" is shifted each  
frame, so we create the impression of a moving grating.  
  
The demo also shows how to use alpha-blending for masking the grating  
with a gaussian transparency mask (a texture with transparency layer).  
  
And finally, we demonstrate rotated drawing, as well as how to emulate  
the old OS-9 'WaitBlanking' command with the new '[Flip](Flip)' command.  
  
### Parameters:  
  
angle = Angle of the grating with respect to the vertical direction.  
cyclespersecond = Speed of grating in cycles per second.  
f = Frequency of grating in cycles per pixel.  
drawmask = If set to 1, then a gaussian aperture is drawn over the grating  
  
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
  
see also: [PsychDemos](PsychDemos), [MovieDemo](MovieDemo)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/PsychTutorials/DriftingMaskedGratingTutorial.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/PsychTutorials/DriftingMaskedGratingTutorial.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/PsychTutorials/DriftingMaskedGratingTutorial.m</code>
</div>

