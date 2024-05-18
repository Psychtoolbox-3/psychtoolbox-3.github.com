# [EyelinkLegacyDoTrackerSetup](EyelinkLegacyDoTrackerSetup)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkBasic](EyelinkBasic)>[EyelinkBasicLegacy](EyelinkBasicLegacy)

USAGE: result=[EyelinkLegacyDoTrackerSetup](EyelinkLegacyDoTrackerSetup)(el [, sendkey])  
  
NOTE: This function is deprecated, unmaintained, and not recommended anymore.  
Use [EyelinkDoTrackerSetup](EyelinkDoTrackerSetup)() for a modern solution instead.  
  
el: Eyelink default values  
  
sendkey:  set to go directly into a particular mode  
          sendkey is optional and ignored if el.callback is defined for  
          callback based tracker setup.  
  
          'v', start validation  
          'c', start calibration  
          'd', start driftcorrection  
          13, or el.ENTER\_KEY, show 'eye' setup image  
  
Note that [EyelinkLegacyDoTrackerSetup](EyelinkLegacyDoTrackerSetup)() internally uses [Beeper](Beeper)() and [Snd](Snd)() to play  
auditory feedback tones if el.targetbeep=1 or el.feedbackbeep=1 and the  
el.callback function is set to the default [PsychEyelinkDispatchCallback](PsychEyelinkDispatchCallback)().  
If you want to use [PsychPortAudio](PsychPortAudio) in a script that also calls [EyelinkLegacyDoTrackerSetup](EyelinkLegacyDoTrackerSetup),  
then read "help [Snd](Snd)" for instructions on how to provide proper interoperation  
between [PsychPortAudio](PsychPortAudio) and the feedback sounds created by Eyelink.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/EyelinkBasicLegacy/EyelinkLegacyDoTrackerSetup.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/EyelinkBasicLegacy/EyelinkLegacyDoTrackerSetup.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/EyelinkBasicLegacy/EyelinkLegacyDoTrackerSetup.m</code>
</div>

