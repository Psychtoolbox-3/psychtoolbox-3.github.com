# [PR655init](PR655init)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[PR655Toolbox](PR655Toolbox)

retval = [PR655init](PR655init)(portNumber, [enableHandshaking])  
  
Initialize serial port for talking to colorimeter.  
Returns whatever character is sent by colorimeter  
  
Per [PhotoResearch](PhotoResearch), handshaking is disabled.  
  
11/26/07    mpr   added timeout if nothing is returned within 10 seconds.  
01/16/09    tbc   Adapted from [PR650Toolbox](PR650Toolbox) for use with PR655  
  
It seems the iterative [CMCheckInit](CMCheckInit) method of initialization is not  
necessary with the PR655, so one run of this seems to do the trick.  
"usbmodem\*" seems to cover every instance I've run into. Not sure about  
the prevalance of using usbmodem as a generic identifier, but if you can  
afford the PR655, you're probably on some more respectable form of internet  
connection. -TBC  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PR655Toolbox/PR655init.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PR655Toolbox/PR655init.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PR655Toolbox/PR655init.m</code>
</div>

