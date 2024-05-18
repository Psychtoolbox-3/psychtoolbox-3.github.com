# [EyeLink_MRI_BlockRecord](EyeLink_MRI_BlockRecord)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkDemos](EyelinkDemos)>[SR-ResearchDemos](SR-ResearchDemos)>[MRI_BlockRecord](MRI_BlockRecord)

Simple MRI demo with [EyeLink](EyeLink) integration.  
6 trials are presented in 2 blocks of 3 trials. Trial duration is 5.5s during which a 4s stimulus is presented.  
A block starts with a drift-check followed by presentation of central crosshairs. Eye movements are recorded while   
waiting for an MRI trigger (keyboard key 't' in this demo). The stimulus is presented when trigger is received.  
A fixed ITI is maintained by presenting crosshairs between each 4s stimulus. Eye movements are recorded throughout  
an entire block rather than on a trial-by-trial basis.   
  
In STEP 5 it is shown how to:  
- shrink the spread of the calibration/validation targets so they are all visible if the MRI bore blocks part of the screen  
- apply an optional online drift correction (see [EyeLink](EyeLink) 1000 Plus User Manual section 3.11.2)  
  
Usage:  
Eyelink\_MRI\_BlockRecord(screenNumber)  
  
screenNumber is an optional parameter which can be used to pass a specific value to [PsychImaging](PsychImaging)('OpenWindow', ...)  
If screenNumber is not specified, or if isempty(screenNumber) then the default:  
screenNumber = max([Screen](Screen)('Screens'));  
will be used.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/MRI_BlockRecord/EyeLink_MRI_BlockRecord.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/MRI_BlockRecord/EyeLink_MRI_BlockRecord.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/MRI_BlockRecord/EyeLink_MRI_BlockRecord.m</code>
</div>

