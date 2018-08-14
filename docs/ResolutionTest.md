# [ResolutionTest](ResolutionTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[ResolutionTest](ResolutionTest) prints screen resolutions reported by [Screen](Screen) 'Resolution'  
and 'Resolutions'.  
  
Usage: [ResolutionTest](ResolutionTest)([screenNumbers=all]);  
  
On Linux, if a Psychtoolbox screen (=X-[Screen](Screen)) has multiple video outputs  
attached, this function will report both, per output settings and modes and  
the unified resolution of a screen - consisting of virtual resolutions and  
settings formed by all attached outputs. Per-Output settings on Linux can  
be made via [Screen](Screen)('ConfigureDisplay', 'Scanout', screenNumber, outputNumber, ...);  
[Screen](Screen)('Resolution', screenNumber, ...); only affects or reports the unified  
"virtual resolution" of a whole X-[Screen](Screen), not of its individual outputs.  
  
Also see [SetResolution](SetResolution), [NearestResolution](NearestResolution), and [Screen](Screen) Resolution and Resolutions.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/ResolutionTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/ResolutionTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/ResolutionTest.m</code>
</div>

