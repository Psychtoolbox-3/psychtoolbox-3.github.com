# [psychassert](psychassert)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[psychassert](psychassert)(expression, ...) - Replacement for Matlab 7 builtin assert().  
This is hopefully useful for older Matlab installations and  
for the Octave port:  
  
If the assert-function is supported as builtin function on  
your Matlab installation, this function will call the builtin  
"real" assert function. Read the "help assert" for usage info.  
  
If your Matlab lacks a assert-function, this function  
will try to emulate the real assert function. The only known limitation  
of our own assert wrt. Matlabs assert is that it can't handle the MSG\_ID  
parameter as 2nd argument. Passing only message strings or message  
formatting strings + variable number of arguments should work.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/psychassert.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/psychassert.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/psychassert.m</code>
</div>

