# [DriftDemo3](DriftDemo3)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

function [DriftDemo3](DriftDemo3)([cyclespersecond=1][, p=32])  
  
Display an animated grating using the new [Screen](Screen)('DrawTexture') command.  
In the [OpenGL](OpenGL)-Psychtoolbox [Screen](Screen)('DrawTexture') replaces  
[Screen](Screen)('CopyWindow'). The demo will stop after 60 seconds have  
passed or after the user hits a key.  
  
This demo illustrates how to draw an animated grating online by use of  
only one grating texture with the minimal amount of code and complexity.  
It is restricted in that the spatial period of the grating in pixels  
must divide the total size of the pattern without remainder and that the  
size of the grating in pixels must be a power of two, e.g., 256 or 512 or  
1024. For a more complex but more general solution which allows for  
arbitrary grating sizes and also masked gratings, see [DriftDemo2](DriftDemo2). For a  
very fast and efficient method, which only works on recent graphics  
hardware, see [DriftDemo4](DriftDemo4).  
  
We create one single texture with a static sine grating. The texture  
is a power-of-two texture, one whose width and height are powers of two.  
  
Such textures can be drawn in a special scrolling mode, as if they  
would extend in each direction to infinity, periodically repeating  
the pattern of the texture image in each direction.  
  
In each successive frame we draw a rectangular region of the sine  
texture onto the screen that is the size of the texture. This region,  
the 'srcRect' in the [Screen](Screen)('DrawTexture') command, is shifted each  
frame. As the graphics hardware makes our special texture to appear as if  
it is repeating infinitely into each direction, we create the impression of  
a moving grating.  
  
### Parameters:  
  
cyclespersecond = Speed of grating in cycles per second.  
p = Spatial period of grating in pixels.  
  
### [CopyWindow](CopyWindow) vs. [DrawTexture](DrawTexture):  
  
In the OS 9 Psychtoolbox, [Screen](Screen) ('CopyWindow") was used for all  
time-critical display of images, in particular for display of the movie  
frames in animated stimuli. In contrast, [Screen](Screen)('DrawTexture') should not  
be used for display of all graphic elements,  but only for  display of  
MATLAB matrices.  For all other graphical elements, such as lines,  rectangles,  
and ovals we recommend that these be drawn directly to the  display  
window during the animation rather than rendered to offscreen  windows  
prior to the animation.  
  
see also: [PsychDemos](PsychDemos), [MovieDemo](MovieDemo), [DriftDemo](DriftDemo), [DriftDemo2](DriftDemo2)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/DriftDemo3.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/DriftDemo3.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/DriftDemo3.m</code>
</div>

