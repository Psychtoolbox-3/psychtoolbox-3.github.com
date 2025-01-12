# [IsARM](IsARM)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

resultFlag = [IsARM](IsARM)([wantTrueHostArch=0])  
  
By default (if wantTrueHostArch omitted or false) returns true if the  
cpu architecture for which Octave or Matlab and Psychtoolbox mex files  
are built is ARM. Otherwise it returns false.  
  
If wantTrueHostArch is true, then return the true machine processor  
architecture of the host computer and operating system. This matters if  
one is running Psychtoolbox on a non-native Octave or Matlab on a ARM  
operating system + machine via some emulation layer, e.g., most commonly  
Octave/Matlab for Apple Intel Macs on an Apple Silicon Mac via Rosetta2  
emulation.  
  
Note: True machine detection is currently only implemented for macOS,  
otherwise we assume scripting runtime architecture == true architecture  
for now.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/IsARM.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/IsARM.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/IsARM.m</code>
</div>

