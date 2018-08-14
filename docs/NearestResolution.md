# [NearestResolution](NearestResolution)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

res=[NearestResolution](NearestResolution)(screenNumber,[width,height,hz,pixelSize])  
res=[NearestResolution](NearestResolution)(screenNumber [,width][,height][,hz][,pixelSize][,outputId])  
res=[NearestResolution](NearestResolution)(screenNumber,desiredRes)  
  
Finds the available screen resolution most similar (in log cartesian space) to that  
requested. Any argument that is [] or [NaN](NaN) will be ignored in assessing similarity.  
If you specify pixelSize then the returned res will specify pixelSize. Typically  
you'll use the returned "res" to set your screen's resolution:  
  
[SetResolution](SetResolution)(screenNumber, res)  
  
Note: On Linux, if more than one video display output is connected to  
a given screenNumber, you must specify the optional 'outputId' parameter  
to select the output for which you want a match.  
  
Also see [SetResolution](SetResolution), [ResolutionTest](ResolutionTest), and [Screen](Screen) Resolution and Resolutions.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/NearestResolution.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/NearestResolution.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/NearestResolution.m</code>
</div>

