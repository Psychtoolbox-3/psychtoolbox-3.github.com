# [EyeLink_FixWindowBufferedSamples](EyeLink_FixWindowBufferedSamples)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkDemos](EyelinkDemos)>[SR-ResearchDemos](SR-ResearchDemos)>[GazeContingent](GazeContingent)>[FixWindowBufferedSamples](FixWindowBufferedSamples)

[EyeLink](EyeLink) gaze-contingent demo that shows how to retrieve online gaze samples from a buffer.  
In each trial central crosshairs are shown until gaze is detected continuously within a central   
square window for 500ms or until the space bar is pressed. An image is   
then presented until the space bar is pressed to end the trial.  
  
Usage:  
Eyelink\_FixWindowBufferedSamples(screenNumber)  
  
screenNumber is an optional parameter which can be used to pass a specific value to [PsychImaging](PsychImaging)('OpenWindow', ...)  
If screenNumber is not specified, or if isempty(screenNumber) then the default:  
screenNumber = max([Screen](Screen)('Screens'));  
will be used.  
  
This demo uses the 'GetNextDataType'/'GetFloatData' function pair that allows access to the following buffered samples and events  
(See [EyeLink](EyeLink) Programmers Guide manual \> Data Structures \> FEVENT):  
  
STARTBLINK 3 (the start of a blink)  
ENDBLINK 4 (the end of a blink)  
STARTSACC 5 (the start of a saccade)  
ENDSACC 6 (the end of a saccade)  
STARTFIX 7 (the start of a fixation)  
ENDFIX 8 (the end of a fixation)  
FIXUPDATE 9 (a fixation update during a fixation)  
SAMPLE\_TYPE 200 (a sample)  
MISSING\_DATA -32768 (missing data)  
  
Use buffered data if you need to:  
a) grab every single consecutive sample online  
b) grab event data (e.g. fixation/saccade/blink events) online  
  
Note that some buffered event data take some time to be available online due to the times involved  
in calculating velocity/acceleration. If you need to retrieve online gaze  
position as fast as possible and/or you don't need to get all subsequent samples or other  
events, then use the Eyelink('NewFloatSampleAvailable') / Eyelink('NewestFloatSample') function pair,  
as illustrated in the [GCfastSamples](GCfastSamples).m example.  
---------------------------------------------------------------------------------------------  
  
Events structure and fields available via the 'GetNextDataType'/'GetFloatData' function pair:  
STARTBLINK, STARTSACC, STARTFIX:  
      type (number assigned to event - STARTBLINK=3, STARTSACC=5, STARTFIX=7)  
      eye (0=left eye, 1=right eye)  
      sttime (event start time)  
  
### ENDBLINK:  
      type (number assigned to event - ENDBLINK=4)  
      eye (0=left eye, 1=right eye)  
      sttime (event start time)  
      entime (event end time)  
  
### ENDSACC:  
      type (number assigned to event - ENDSACC=6)  
      eye (0=left eye, 1=right eye)  
      sttime (event start time)  
      entime (event end time)  
      gstx (Saccade start x gaze position)  
      gsty (Saccade start y gaze position)  
      genx (Saccade end x gaze position)  
      geny (Saccade end y gaze position)  
      supd\_x (Saccade start x 'pixel per degree' value)  
      supd\_y (Saccade start y 'pixel per degree' value)  
      eupd\_x (Saccade end x 'pixel per degree' value)  
      eupd\_y (Saccade end y 'pixel per degree' value)  
  
FIXUPDATE, ENDFIX:  
      type (number assigned to event - FIXUPDATE=9, ENDFIX=8)  
      eye (0=left eye, 1=right eye)  
      sttime (event start time)  
      entime (event end time)  
      gavx (average gaze x position during fixation)  
      gavy (average gaze y position during fixation)  
      ava (average pupil size)  
      supd\_x (Fixation start x 'pixel per degree' value)  
      supd\_y (Fixation start y 'pixel per degree' value)  
      eupd\_x (Fixation end x 'pixel per degree' value)  
      eupd\_y (Fixation end y 'pixel per degree' value)  
  
SAMPLE\_TYPE  
      time (sample time)  
      type (SAMPLE=200)  
      pa ([lef eye pupil size, right eye pupil size])  
      gx ([left gaze x, right gaze x])  
      gy ([left gaze y, right gaze y])  
      rx (x 'pixel per degree' value)  
      ry (y 'pixel per degree' value)  
      buttons (button state and changes)  
      hdata (contains a list of 8 fields. Only the first 4 values are important:  
            [uncalibrated target sticker x, uncalibrated target sticker y, target sticker distance in mm, target flags)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/GazeContingent/FixWindowBufferedSamples/EyeLink_FixWindowBufferedSamples.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/GazeContingent/FixWindowBufferedSamples/EyeLink_FixWindowBufferedSamples.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkDemos/SR-ResearchDemos/GazeContingent/FixWindowBufferedSamples/EyeLink_FixWindowBufferedSamples.m</code>
</div>

