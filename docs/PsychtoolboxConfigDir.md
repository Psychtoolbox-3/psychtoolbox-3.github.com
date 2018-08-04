# [PsychtoolboxConfigDir](PsychtoolboxConfigDir)
##### >[Psychtoolbox](Psychtoolbox)>[PsychFiles](PsychFiles)

Syntax: path=[PsychtoolboxConfigDir](PsychtoolboxConfigDir)([subDir])  
  
Purpose: Look for a folder for storing Psychtoolbox preferences; create if  
         necessary.  
  
         When called without optional 'subDir' argument, the path to the  
         root configuration folder is returned (and the folder optionally  
         created if it doesn't exist yet). When 'subDir' is given, the  
         path to the subfolder 'subDir' inside the root configuration  
         folder is returned - and the 'subDir' created inside that folder  
         if neccessary. Subfolders are useful to group related  
         configuration data, e.g., all settings for DAQ toolbox, all  
         display calibration settings, etc.  
  
History: 1/23/08    mpr configured it was about time to write this  
         3/7/08     mpr streamlined this  
         3/8/08     mk  A bit more of streamlining - Don't write the  
                        [PsychPrefsfolder](PsychPrefsfolder).m file anymore.  
         4/28/08    mk  Made compatible with Octave, added 'subDir'  
                        option.  
         6/14/09    mk  Remove Octave code -\> Not needed anymore.  
         4/10/17    mk  Some cleanup and error reporting improvements.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychFiles/PsychtoolboxConfigDir.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychFiles/PsychtoolboxConfigDir.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychFiles/PsychtoolboxConfigDir.m</code>
</div>

