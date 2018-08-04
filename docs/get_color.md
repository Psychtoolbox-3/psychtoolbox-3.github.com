# [get_color](get_color)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)>[Utilities](Utilities)

Syntax: [ColorVector](ColorVector) = get\_color[(ColorNameString)]((ColorNameString))  
  
convert color name to color triple. Color name/triple combinations  
were taken from the Unix X11/R4 rgb.txt file and converted to  
a format matlab would properly interpret.  This function was  
created by Mickey P. Rowe some time around 1993 or 1994.  In June of 2000  
I found out that the switch statement could be used instead of successive   
calls to strcmp.  I suspect that the compiled version is identical, but this  
looks more elegant.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/Utilities/get_color.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/Utilities/get_color.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/Utilities/get_color.m</code>
</div>

