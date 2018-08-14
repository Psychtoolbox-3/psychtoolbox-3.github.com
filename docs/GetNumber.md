# [GetNumber](GetNumber)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

number = [GetNumber](GetNumber)([deviceIndex][, untilTime=inf][, optional [KbCheck](KbCheck) arguments...])  
  
Get a number typed at the keyboard. Entry is terminated by  
<return\> or <enter\>. Typed keys are not echoed. Useful for  
i/o in a [Screen](Screen) window. Equivalent to "number=str2num[(GetString)]((GetString))".  
  
Returns the empty matrix if no number is entered. Returns a  
column vector with multiple numbers if more than one number  
is entered.  
  
See also: [GetEchoNumber](GetEchoNumber), [GetString](GetString), [GetEchoString](GetEchoString)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/GetNumber.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/GetNumber.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/GetNumber.m</code>
</div>

