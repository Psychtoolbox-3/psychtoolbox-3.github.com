# [MakeBeep](MakeBeep)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

[beep,samplingRate] = [MakeBeep](MakeBeep)(freq,duration,[samplingRate])  
  
Compute array that can be used by [Snd](Snd) to produce a pure tone of specified  
"freq" (Hz) and "duration" (s). The "samplingRate" defaults to  
[Snd](Snd)('DefaultRate').  
  
    beep = [MakeBeep](MakeBeep)(freq,duration);  
    [Snd](Snd)('Open');  
    .... do some stuff ....  
    [Snd](Snd)('Play',beep);  
  
See [Snd](Snd).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/MakeBeep.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/MakeBeep.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/MakeBeep.m</code>
</div>

