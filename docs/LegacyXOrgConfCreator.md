# [LegacyXOrgConfCreator](LegacyXOrgConfCreator)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[LegacyXOrgConfCreator](LegacyXOrgConfCreator) - Automatically create X11 config files for old X-Servers.  
  
This it the legacy version for X-Server 1.20 and earlier, Mesa 21.x and earlier,  
running Linux 5.14 and earlier. It gets called by [XOrgConfCreator](XOrgConfCreator) on such older  
setups. The plan is to not touch this file in the future anymore.  
  
This friendly little setup assistant will analyze your systems graphics  
card and display setup, then ask you questions about how you want your  
display setup configured. Then it will create a configuration file to  
setup your displays in the desired way after the next logout -\> login  
cycle, or after the next reboot of your machine.  
  
Files are stored by default in a configuration directory where the  
[XOrgConfSelector](XOrgConfSelector) helper script can find and apply them.  
  
Please note that this assistant can't yet handle systems with multiple  
active graphics cards properly. It is only for regular single graphics  
card setups or hybrid graphics laptops with one active graphics card.  
  
In order for the assistant to detect and handle all potentially useful  
displays you must have all of them connected and active at the time the  
assistant is run.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/LegacyXOrgConfCreator.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/LegacyXOrgConfCreator.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/LegacyXOrgConfCreator.m</code>
</div>

