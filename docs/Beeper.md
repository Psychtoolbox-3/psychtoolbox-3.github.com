# [Beeper](Beeper)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

function [Beeper](Beeper)(frequency, [fVolume], [durationSec]);  
  
Play a beep sound.  Default is 400 Hz for .15 sec.  
frequency can be a number, or else the string 'high', 'med', or 'low'.  
  
fVolume - normalized to range of 0 - 1.  Default is 0.4;    
Warning:  1 is the maximum volume and is often very loud!  
  
NOTE: [Beeper](Beeper)() uses [Snd](Snd)() internally. If you want to use [Beeper](Beeper)() - and therefore  
[Snd](Snd)() in parallel with [PsychPortAudio](PsychPortAudio), read the notes in "help [Snd](Snd)" about pahandle  
sharing!  
  
Funny name is because Matlab 6 contains a built-in function called "beep".  
  
2006-02-15 - cburns  
  -   Added fVolume param  
  -   Swapped parameter order  
  
2006-02-02 - cburns  
  -   Scaled down the volume of the sound to match the system volume better.  It was at maximum volume.  
      Would scare you enough to rip the bite bar off it's mount!  
      And switched to useing the sound() function, instead of the soundsc() function  
      which, by default, maximizes the volume.  
  -   Update, using the [PsychToolbox](PsychToolbox) [Snd](Snd) function which should return immediately.  
      Were experiencing delays with sound function  
  
12/2/00 Backus - original version  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/Beeper.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/Beeper.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/Beeper.m</code>
</div>

