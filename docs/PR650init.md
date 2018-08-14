# [PR650init](PR650init)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[PR650Toolbox](PR650Toolbox)

retval = [PR650init](PR650init)(portNumber, [enableHandshaking])  
  
Initialize serial port for talking to colorimeter.  
Returns whatever character is sent by colorimeter  
  
'enableHandshaking' allows you to enable handshaking.  By default,  
handshaking is disabled.  To enable handshaking, set this value to 1 or  
true.  
  
11/26/07    mpr   added timeout if nothing is returned within 10 seconds.  
  
In my experience, calling this function directly leads to poor performance  
(usually no communication is ever established).  You should find the function  
[CMCheckInit](CMCheckInit) in the [PsychHardware](PsychHardware) folder, one folder up the tree from this one  
(which is presumably [PR650Toolbox)](PR650Toolbox)).  Calling this function from [CMCheckInit](CMCheckInit)  
should provide more reliable establishment of contact and hints on what to   
try if contact fails.  -- MPR  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PR650Toolbox/PR650init.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PR650Toolbox/PR650init.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PR650Toolbox/PR650init.m</code>
</div>

