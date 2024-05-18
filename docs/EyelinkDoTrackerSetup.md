# [EyelinkDoTrackerSetup](EyelinkDoTrackerSetup)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkBasic](EyelinkBasic)

USAGE: result=[EyelinkDoTrackerSetup](EyelinkDoTrackerSetup)(el [, sendkey])  
  
el: Eyelink default values  
  
sendkey:  set to go directly into a particular mode  
          sendkey is optional and ignored if el.callback is defined for  
          callback based tracker setup.  
  
          'v', start validation  
          'c', start calibration  
          'd', start driftcorrection  
          13, or el.ENTER\_KEY, show 'eye' setup image  
  
Note that [EyelinkDoTrackerSetup](EyelinkDoTrackerSetup)() internally may use [Snd](Snd)() to play  
auditory feedback tones if el.targetbeep=1 or el.feedbackbeep=1 and the  
el.callback function is set to the default [PsychEyelinkDispatchCallback](PsychEyelinkDispatchCallback)().  
  
If you want to use [PsychPortAudio](PsychPortAudio) in a script that also calls [EyelinkDoTrackerSetup](EyelinkDoTrackerSetup),  
then read "help [Snd](Snd)" for instructions on how to provide proper interoperation  
between [PsychPortAudio](PsychPortAudio) and the feedback sounds created by Eyelink. The demos  
referenced under "help SR-[ResearchDemos](ResearchDemos)" show an even better approach than the  
one described in "help [Snd](Snd)".  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/EyelinkDoTrackerSetup.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/EyelinkDoTrackerSetup.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/EyelinkDoTrackerSetup.m</code>
</div>

