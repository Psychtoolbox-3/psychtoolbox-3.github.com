# [overrideBuiltInFunction](overrideBuiltInFunction)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

Method to override a MATLAB built-in function with a user-supplied function   
with the same name. The way this works is that it replaces the built-in function  
with a function handle parameter whose name matches that of the overriden  
function.  
  
Usage:  
      functionName = overrideBuiltInFunction('functionName', overridingFunctionPath);  
  
      where the overridingFunctionPath string can be the full path to the overriding  
      function or a uniquely-identifying subset of the full path.  
  
      This call must be done in the script where you will use the override.   
      To use across several scripts, make it a global function handle:  
  
      global functionName  
      functionName = overrideBuiltInFunction('functionName', overridingFunctionPath);  
  
Example Usage:   
      Override Matlab's built-in function lab2xyz with the one supplied by ISETBIO  
      located in '/Users/Shared/Matlab/Toolboxes/ISETBIO/isettools/color/transforms'  
  
      lab2xyz = overrideBuiltInFunction('lab2xyz', 'isetbio');  
  
Test that it works:  
      clear all  
      functions(@lab2xyz)  
      lab2xyz = overrideBuiltInFunction('lab2xyz', 'isetbio');  
      functions(lab2xyz)  
  
Undoing the override:  
      To 'unoverride', simply clear the function handle. This should bring back  
      the built-in function, e.g.:  
  
      clear lab2xyz  
  
  
10/9/2014   NPC  Wrote it.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/overrideBuiltInFunction.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/overrideBuiltInFunction.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/overrideBuiltInFunction.m</code>
</div>

