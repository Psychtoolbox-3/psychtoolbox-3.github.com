# [SetResolution](SetResolution)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

oldRes=[SetResolution](SetResolution)(screenNumber,width,height,[hz],[pixelSize])  
oldRes=[SetResolution](SetResolution)(screenNumber,res)  
  
Set the resolution of the screen.  This is intended to be used in  
programs that run psychophysical experiments, so [SetResolution](SetResolution) is  
strict. It issues a fatal error unless it can provide exactly the  
resolution you specified. (For lenience, look at [NearestResolution](NearestResolution).)  
  
"screenNumber" is the screen number.  
  
"width" and "height" are the desired dimensions in pixels.    
  
"hz" is the desired refresh rate (default is current frame rate).    
  
"pixelSize" 8, 16, 24, or 32 bits and defaults to current pixelSize.  
On modern operating systems, you should leave "pixelSize" alone, as  
often there will be only one good choice anyway, which is already set  
as the default, so changing it will usually change it for the worse!  
  
Returns the current resolution as "oldRes".    
  
  oldRes=[SetResolution](SetResolution)(0,1024,768,75);  
  w=[Screen](Screen)(0,'OpenWindow');  
  [Screen](Screen)(w,'PutImage',image);  
  [Screen](Screen)(w,'[Close](Close)');  
  [SetResolution](SetResolution)(0, oldRes);  
  
To display a list of available resolutions, try [ResolutionTest](ResolutionTest). Also see  
[NearestResolution](NearestResolution), [ResolutionTest](ResolutionTest), and [Screen](Screen)('Resolution')  
and [Screen](Screen)('Resolutions').  
  
NOTE: Apple has all the new LCD screens return a frame rate of 0, so  
we treat that value as a special case. A request for "hz" of [NaN](NaN) will  
match only with a frame rate of 0.  
  
NOTE: On Linux/X11 this only works as you'd expect if there is only one  
video output connected to a given Psychtoolbox screen / X-[Screen](Screen). On a  
setup with multiple outputs per screen, this will only change the  
size of the framebuffer, but not the resolution of the actual displays!  
Use [Screen](Screen)('ConfigureDisplay', 'Scanout', ...); to change settings on  
such a multi-display per screen setup on Linux.  
  
Originally written by Sabina Wolfson.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/SetResolution.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/SetResolution.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/SetResolution.m</code>
</div>

