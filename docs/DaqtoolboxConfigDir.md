# [DaqtoolboxConfigDir](DaqtoolboxConfigDir)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[Daq](Daq)

Syntax: [AbsolutePath](AbsolutePath) = [DaqtoolboxConfigDir](DaqtoolboxConfigDir)  
  
Purpose: Look for (create if necessary) folder containing preferences for Daq  
         toolbox;  
  
History: 1/28/08  mpr configured this was needed  
         3/7/08   mpr streamlined this  
  
Function does not assume that user is using Psychophysics toolbox, but will  
subordinate Daqtoolbox if that assumption is correct.  That is, function will  
look for Daqtoolbox preferences in a folder containing Psychtoolbox  
preferences.  It will create its own folder iff it does not find one, and that  
folder will be in the Psychtoolbox preferences folder if that folder exists.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/Daq/DaqtoolboxConfigDir.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/Daq/DaqtoolboxConfigDir.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/Daq/DaqtoolboxConfigDir.m</code>
</div>

