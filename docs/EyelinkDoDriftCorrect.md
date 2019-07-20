# [EyelinkDoDriftCorrect](EyelinkDoDriftCorrect)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkBasic](EyelinkBasic)

USAGE: result=[EyelinkDoDriftCorrect](EyelinkDoDriftCorrect)(el [, x, y, draw, allowsetup])  
  
el: eyelink default values  
x,y: position of driftcorrection target  
draw: set to 1 to draw driftcorrection target  
allowsetup: set to 1 to allow to go in to go to trackersetup  
  
Note that [EyelinkDoDriftCorrect](EyelinkDoDriftCorrect)() internally uses [Beeper](Beeper)() and [Snd](Snd)() to play  
auditory feedback tones if el.targetbeep=1 or el.feedbackbeep=1 and the  
el.callback function is set to the default [PsychEyelinkDispatchCallback](PsychEyelinkDispatchCallback)().  
If you want to use [PsychPortAudio](PsychPortAudio) in a script that also calls [EyelinkDoDriftCorrect](EyelinkDoDriftCorrect),  
then read "help [Snd](Snd)" for instructions on how to provide proper interoperation  
between [PsychPortAudio](PsychPortAudio) and the feedback sounds created by Eyelink.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/EyelinkDoDriftCorrect.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/EyelinkDoDriftCorrect.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/EyelinkDoDriftCorrect.m</code>
</div>

