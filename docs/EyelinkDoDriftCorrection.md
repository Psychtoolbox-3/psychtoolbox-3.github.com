# [EyelinkDoDriftCorrection](EyelinkDoDriftCorrection)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[EyelinkToolbox](EyelinkToolbox)>[EyelinkBasic](EyelinkBasic)

success=[EyelinkDoDriftCorrection](EyelinkDoDriftCorrection)(el [, x][, y][, draw][, allowsetup])  
  
### DO PRE-TRIAL DRIFT CORRECTION  
We repeat if ESC key pressed to do setup.  
Setup might also have erased any pre-drawn graphics.  
  
Note that [EyelinkDoDriftCorrection](EyelinkDoDriftCorrection)() internally uses [Beeper](Beeper)() and [Snd](Snd)() to play  
auditory feedback tones if el.targetbeep=1 or el.feedbackbeep=1 and the  
el.callback function is set to the default [PsychEyelinkDispatchCallback](PsychEyelinkDispatchCallback)().  
If you want to use [PsychPortAudio](PsychPortAudio) in a script that also calls [EyelinkDoDriftCorrection](EyelinkDoDriftCorrection),  
then read "help [Snd](Snd)" for instructions on how to provide proper interoperation  
between [PsychPortAudio](PsychPortAudio) and the feedback sounds created by Eyelink.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/EyelinkDoDriftCorrection.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/EyelinkDoDriftCorrection.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/EyelinkToolbox/EyelinkBasic/EyelinkDoDriftCorrection.m</code>
</div>

