# [EyeLink_SimpleVideo](EyeLink_SimpleVideo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkDemos](EyelinkDemos)>[SR-ResearchDemos](SR-ResearchDemos)>[SimpleVideo](SimpleVideo)

Simple video demo with [EyeLink](EyeLink) integration and animated calibration / drift-check/correction targets.  
In each trial eye movements are recorded while a video stimulus is presented on the screen.  
Each trial ends when the space bar is pressed or the video stops playing. A different drift-check/correction  
animated target is used in each of the 2 trials.  
  
Illustrates how a video file can be added for trial play back in Data Viewer's "Trial Play Back Animation" view.   
  
Usage:  
Eyelink\_SimpleVideo(screenNumber)  
  
screenNumber is an optional parameter which can be used to pass a specific value to [PsychImaging](PsychImaging)('OpenWindow', ...)  
If screenNumber is not specified, or if isempty(screenNumber) then the default:  
screenNumber = max([Screen](Screen)('Screens'));  
will be used.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/SimpleVideo/EyeLink_SimpleVideo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/SimpleVideo/EyeLink_SimpleVideo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/SimpleVideo/EyeLink_SimpleVideo.m</code>
</div>

