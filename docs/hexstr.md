# [hexstr](hexstr)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

str=[hexstr](hexstr)(n)  
Convert any number to a hex string representing the lower 32 bits,  
emulating the C format %lx for a long. This works with both positive and  
negative numbers, unlike the MATLAB format %x (and %tx and %bx) which  
can't deal with negative numbers.  
  
fprintf('Error 0x%s.\n',[hexstr](hexstr)(err));  
  
See also DEC2HEX, FPRINTF.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/hexstr.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/hexstr.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/hexstr.m</code>
</div>

