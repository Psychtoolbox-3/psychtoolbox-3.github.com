# [SwitchToNewPsychtoolboxHoster](SwitchToNewPsychtoolboxHoster)
##### >[Psychtoolbox](Psychtoolbox)

Switch a installed Psychtoolbox working copy to our new host [GoogleCode](GoogleCode).  
  
This function checks if the currently installed Psychtoolbox working copy  
is still attached to Berlios code hosting. If so, it tries to switch it  
over to our new code hosting provider [GoogleCode](GoogleCode). Otherwise it does  
nothing.  
  
This function is called by the [PsychtoolboxPostInstallRoutine](PsychtoolboxPostInstallRoutine) after each  
invocation of [DownloadPsychtoolbox](DownloadPsychtoolbox), [UpdatePsychtoolbox](UpdatePsychtoolbox) or [SetupPsychtoolbox](SetupPsychtoolbox).  
It takes care of the transition.  
  
The function can also be called manually by users in the year 2012 and  
later, when the standard installation and update routines do no longer  
work due to Berlios servers being offline.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/SwitchToNewPsychtoolboxHoster.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/SwitchToNewPsychtoolboxHoster.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/SwitchToNewPsychtoolboxHoster.m</code>
</div>

