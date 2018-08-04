# [WlsToT](WlsToT)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

T = [WlsToT](WlsToT)(wls,[sd])  
  
Produce the identity color matching matrix associated  
with the passed wavelength sampling.  
  
Arguments may be either [start delta n] description or  
a list of wavelengths.  
  
The second input sd is the standard deviation of a Gaussian  
blur function which may be incorporated into the T matrix  
if desired.  
  
This second feature should be used with some  
caution, as I haven't thought it completely through.  The  
current implementation normalizes each row of T so that the  
entries sum to 1.  This seems as if it is what we want to  
get answers consistent with what we get when we don't  
incorporate wavelength blurring.  
  
7/11/03  dhb  A few comments added.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/WlsToT.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/WlsToT.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/WlsToT.m</code>
</div>

