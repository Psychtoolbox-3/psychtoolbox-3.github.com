# [EyeLink_StereoPicture](EyeLink_StereoPicture)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkDemos](EyelinkDemos)>[SR-ResearchDemos](SR-ResearchDemos)>[StereoPicture](StereoPicture)

[EyeLink](EyeLink) integration demo for stereo presentation.  
Records eye movements passively while presenting a stereo stimulus. Supports both split-screen mode   
and dual-monitor setup.  
Each trial ends when the space bar is pressed.  
Data Viewer integration with both left and right eyes superimposed on the same eye window view  
  
Usage:  
Eyelink\_StereoPicture(stereoMode, screenNumber)  
  
------------------------------------------------------------  
Supported stereoMode parameters:  
  
Default: 4 == Split-screen mode. Free fusion (lefteye=left, righteye=right): This - together with a screenid of zero - is what you'll want   
to use on MS-Windows with dual-display setups for stereo output.  
  
5 == Split-screen mode. Cross fusion (lefteye=right ...)  
  
10 == Dual-Window stereo: Open two onscreen windows on two monitors, first one will  
display left-eye view, 2nd one right-eye view. Direct all drawing and  
flip commands to the first window, PTB will take care of the rest. This  
mode is mostly useful for dual-display stereo on [MacOS](MacOS)/X. It only works  
on reasonably modern graphics hardware, will abort with an error on  
unsupported hardware.  
------------------------------------------------------------  
  
screenNumber is an optional parameter which can be used to pass a specific value to [PsychImaging](PsychImaging)('OpenWindow', ...)  
If screenNumber is not specified, or if isempty(screenNumber) then the default:  
screenNumber = max([Screen](Screen)('Screens'));  
will be used.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/StereoPicture/EyeLink_StereoPicture.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/StereoPicture/EyeLink_StereoPicture.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/StereoPicture/EyeLink_StereoPicture.m</code>
</div>

