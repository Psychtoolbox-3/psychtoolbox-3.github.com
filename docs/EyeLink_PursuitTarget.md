# [EyeLink_PursuitTarget](EyeLink_PursuitTarget)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkDemos](EyelinkDemos)>[SR-ResearchDemos](SR-ResearchDemos)>[PursuitTarget](PursuitTarget)

A smooth pursuit [EyeLink](EyeLink) integration demo that records eye movements  
while a target moves sinusoidally across the screen. Each trial ends after 5s.  
  
Illustrates how to:  
  - change the drift-check/correction target location before each trial  
  - create a moving target for Data Viewer's Play Back Animation view  
  - create dynamic target location for Data Viewer's Temporal Graph view and sample reports  
  - create target dynamic interest areas for Data Viewer  
  
Usage:  
Eyelink\_PursuitTarget(screenNumber)  
  
screenNumber is an optional parameter which can be used to pass a specific value to [PsychImaging](PsychImaging)('OpenWindow', ...)  
If screenNumber is not specified, or if isempty(screenNumber) then the default:  
screenNumber = max([Screen](Screen)('Screens'));  
will be used.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/PursuitTarget/EyeLink_PursuitTarget.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/PursuitTarget/EyeLink_PursuitTarget.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/PursuitTarget/EyeLink_PursuitTarget.m</code>
</div>

