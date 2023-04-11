# [VideoRefreshFromMeasurement](VideoRefreshFromMeasurement)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

ifi = [VideoRefreshFromMeasurement](VideoRefreshFromMeasurement)(window [, samples=600]);  
  
Measure video refresh interval for onscreen windows display with a method  
that is supposed to be as robust and accurate as possible.  
  
'window' is the onscreen window handle for the window whose corresponding  
display should be measured.  
  
'samples' is the (optional) number of refresh samples to take into  
account.  
  
This routine returns the estimated refresh duration in seconds. It uses  
one of multiple calibration strategies, preferring more accurate ones but  
falling back to less accurate ones if the accurate ones are not supported  
by your system:  
  
1. On [MacOS](MacOS)/X it tries to use low-level VBL interrupt timestamps.  
2. If that fails it tries to get the measurement from the beamposition  
   measurement method.  
3. If that fails it returns the measurement from  
   [Screen](Screen)('GetFlipInterval').  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/VideoRefreshFromMeasurement.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/VideoRefreshFromMeasurement.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/VideoRefreshFromMeasurement.m</code>
</div>

