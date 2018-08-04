# [StandaloneTimingTest](StandaloneTimingTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[StandaloneTimingTest](StandaloneTimingTest)(use\_sigsetjmp, savemask)  
  
run a timing loop in a separate process, indepenent of MATLAB.  plot the results.    
  
use\_sigsetmask specifies whether the [StandaloneTimingTest](StandaloneTimingTest) program will  
call sigsetjmp() within the timing loop.  If sigsetmask is set, then   
[StandaloneTimingTest](StandaloneTimingTest) passes savemask to sigsetjmp in the second argument.  
  
comparing results of [StandaloneTimingTest](StandaloneTimingTest) with and without  
sigsetjmp shows that calling sigsetjmp with the savemask  
argument set causes OS X to suspend execution of the [StandaloneTimingTest](StandaloneTimingTest)  
application for up to 13 ms.  
  
SEE ALSO: [StandaloneTimingTest](StandaloneTimingTest).c  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/StandaloneTimingTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/StandaloneTimingTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/StandaloneTimingTest.m</code>
</div>

