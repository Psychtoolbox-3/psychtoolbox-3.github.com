# [AutoBrightness](AutoBrightness)
##### >[Psychtoolbox](Psychtoolbox)>[PsychContributed](PsychContributed)>[AutoBrightness](AutoBrightness)

[oldSetting, status] = [AutoBrightness](AutoBrightness)([screenNumber=0][, newSetting])  
  
OBSOLETE: Use [MacDisplaySettings](MacDisplaySettings) instead. It's faster and more reliable.  
To support old programs we have rewritten this to simply call  
[MacDisplaySettings](MacDisplaySettings). However, it's probably best to replace your call to  
[AutoBrightness](AutoBrightness) by your own call to [MacDisplaySettings](MacDisplaySettings), using what's below  
as a model. If you need [AutoBrightness](AutoBrightness) you probably also need more of the  
controls offered by [MacDisplaySettings](MacDisplaySettings).  
  
AUTOBRIGHTNESS. Get and set the "Automatically adjust brightness"  
checkbox on the Mac OS X: System Preferences: Displays panel. The  
function argument "newSetting" (integer 0 or 1) indicates whether you  
want to turn the autobrightness feature on (newSetting==1) or off  
(newSetting==0). If you call without an argument (or anything other than  
0 or 1) then nothing is changed. The current state is always reported in  
the returned oldSetting (0 or 1). The optionally returned "status" is  
always zero unless the applescript failed.  
  
HISTORY: Written by denis.pelli@nyu.edu for the Psychtoolbox, May 21,  
2015. Incorporated into MATLAB adding untested code to specify which  
screen, by Mario Kleiner, June 1. Convert return argument from string to  
double, by Denis, June 11, 2015. Replaced by a call to the new  
[MacDisplaySettings](MacDisplaySettings) (as suggested by Mario) Denis Pelli, May 6, 2020.  
  
See also:  
[MacDisplaySettings](MacDisplaySettings).m  
May 6, 2020, denis.pelli@nyu.edu  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychContributed/AutoBrightness/AutoBrightness.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychContributed/AutoBrightness/AutoBrightness.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychContributed/AutoBrightness/AutoBrightness.m</code>
</div>

