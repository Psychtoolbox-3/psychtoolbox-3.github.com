# [LoadGenerator](LoadGenerator)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[LoadGenerator](LoadGenerator)([yieldmsecs=0])  
  
Create cpu-load by simply executing an empty while-loop as fast as  
possible.  
  
Optionally the load can be reduced by specifying a non-zero 'yieldmsecs'  
argument telling the function that it should release the cpu for  
'yieldmsecs' milliseconds in each loop iteration.  
  
This function never returns, you have to abort it by pressing CTRL+C.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/LoadGenerator.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/LoadGenerator.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/LoadGenerator.m</code>
</div>

