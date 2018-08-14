# [PR705write](PR705write)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[PR705Toolbox](PR705Toolbox)

[PR705write](PR705write) - Write a string of characters to the PR-705.  
  
Syntax:  
varargout = [PR705write](PR705write)(cmdStr [, block=1])  
  
Description:  
This is a convenience wrapper to write data to the PR-705 device. Aside  
from appending a carriage return and not requiring an explicit port  
handle, this function is identical to IOPort's Write (see [IOPort](IOPort) Write?   
for more details).  
  
Inputs:  
datastr (1xN char) - data string to write to the PR-705.  
block (scalar) - enable (1, default) or disable (0) blocking writes  
  
Outputs:  
Refer to [IOPort](IOPort) Write?  
  
11/29/12    zlb   Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PR705Toolbox/PR705write.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PR705Toolbox/PR705write.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PR705Toolbox/PR705write.m</code>
</div>

