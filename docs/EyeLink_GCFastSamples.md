# [EyeLink_GCFastSamples](EyeLink_GCFastSamples)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkDemos](EyelinkDemos)>[SR-ResearchDemos](SR-ResearchDemos)>[GazeContingent](GazeContingent)>[GCFastSamples](GCFastSamples)

A simple [EyeLink](EyeLink) gaze-contingent demo showing how to retrieve fast online samples.  
In each trial an image is presented with a red gaze-contingent dot overlaid on top.  
The dot's location is updated online based on the x y coordinates of the latest gaze sample retrieved online.  
Each trial ends when the space bar is pressed.  
  
Usage:  
Eyelink\_GCfastSamples(screenNumber)  
  
screenNumber is an optional parameter which can be used to pass a specific value to [PsychImaging](PsychImaging)('OpenWindow', ...)  
If screenNumber is not specified, or if isempty(screenNumber) then the default:  
screenNumber = max([Screen](Screen)('Screens'));  
will be used.  
  
The demo checks if a new sample is available online via the link. This is the most recent sample, which is faster than buffered data.  
This is equivalent to eyeLink\_newest\_float\_sample() in C API. See [EyeLink](EyeLink) Programmers Guide manual \> Function Lists \> Message and Command Sending/Receiving \> Functions  
It allows access to the following sample properties:  
  
      time (sample time)  
      type (SAMPLE=200)  
      gx ([left gaze x, right gaze x])  
      gy ([left gaze y, right gaze y])  
      pa ([lef eye pupil size, right eye pupil size])  
      rx (x 'pixel per degree' value)  
      ry (y 'pixel per degree' value)  
      buttons (button state and changes)  
      hdata (contains a list of 8 fields. Only the first 4 values are important:  
            [uncalibrated target sticker x, uncalibrated target sticker y, target sticker distance in mm, target flags)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/GazeContingent/GCFastSamples/EyeLink_GCFastSamples.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/GazeContingent/GCFastSamples/EyeLink_GCFastSamples.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/GazeContingent/GCFastSamples/EyeLink_GCFastSamples.m</code>
</div>

