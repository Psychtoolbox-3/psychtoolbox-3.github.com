# [IsStartUpdateImplantedInFinish](IsStartUpdateImplantedInFinish)
##### >[Psychtoolbox](Psychtoolbox)>[PsychInitialize](PsychInitialize)

isImplanted=[IsStartUpdateImplantedInFinish](IsStartUpdateImplantedInFinish)  
  
OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Return TRUE if both the finish.m file is on the MATLAB path and if it   
includes a call to [StartUpdateProcess](StartUpdateProcess).  
  
The OS X update process causes suspension of MATLAB for up to about 13ms  
at 30-second intervals.  Psychtoolbox functions [Rush](Rush) and [Priority](Priority)  
automatically kill and restart the update process when priority is,  
respectively, raised above 0 and lowered back to 0.  To insure that the  
update process is restored when MATLAB exits we add a call to  
[StartUpdateProcess](StartUpdateProcess) to the finish.m file which MATLAB calls before  
exiting. If multiple finish.m files exist on the MATLAB path then  MATLAB  
seems to invoke only the first one which it finds in the path search  
order as reported by the "path" command or as shown in the "set path"  
window.  
  
The Psychtoolbox includes the file:  
  Psychtoolbox/[PsychInitialize](PsychInitialize)/finish.m  
  
Because it is possible that users could modify path settings to include a  
custom finish.m file ahead of the Psychtoolbox finish.m file in the  
MATLAB path, we check that the finish.m file includes the  
[StartUpdateProcess](StartUpdateProcess) call.   
  
Neither [Rush](Rush) not [Priority](Priority) will raise the priorty above 0 if  
[IsStartUpdatedImplantedInFinsh](IsStartUpdatedImplantedInFinsh) returns FALSE.  This helps is a precaution  
against exiting MATLAB and leaving the update process shut down. However,  
it is not foolproof.  If MATLAB crashes while priority is \>0 then it will  
not restart update on quitting.    
  
If you have your own finish.m file which you want to use, then place it  
ahead of the Psychtoolbox finish.m file on MATLAB's search path and add  
to your file the line:  
  [StartUpdateProcess](StartUpdateProcess);     %Restore the system update process.  
  
OS 9: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[IsStartUpdateImplantedInFinish](IsStartUpdateImplantedInFinish) does not exist in OS 9.   
  
WINDOWS:\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[IsStartUpdateImplantedInFinish](IsStartUpdateImplantedInFinish) does not exist in Windows.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
see also: finish, [StartUpdateProcess](StartUpdateProcess), [KillUpdateProcess](KillUpdateProcess), [Priority](Priority), [Rush](Rush).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychInitialize/IsStartUpdateImplantedInFinish.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychInitialize/IsStartUpdateImplantedInFinish.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychInitialize/IsStartUpdateImplantedInFinish.m</code>
</div>

