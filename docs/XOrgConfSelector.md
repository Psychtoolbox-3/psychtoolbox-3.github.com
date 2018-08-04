# [XOrgConfSelector](XOrgConfSelector)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[XOrgConfSelector](XOrgConfSelector)([sdir]) - Select a X11 configuration file to apply.  
  
By default configuration files are chosen from a [PsychtoolboxConfigDir](PsychtoolboxConfigDir)  
subfolder, where [XOrgConfCreator](XOrgConfCreator) creates and stores them by default.  
  
You can override the choice of the directory for config files by  
providing the optional 'sdir' argument with the path to a different  
folder.  
  
The chosen configuration file is copied into the systems  
/etc/X11/xorg.conf.d/ folder for the X-Server to pick it up and apply it  
during the next logout-\>login cycle or restart.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/XOrgConfSelector.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/XOrgConfSelector.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/XOrgConfSelector.m</code>
</div>

