# [AssertMex](AssertMex)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

Handle missing or dysfunctional MEX files on Matlab or Octave.  
  
[AssertMex](AssertMex)(targetname)  
  
[AssertMex](AssertMex) detects missing mex files.  Calling [AssertMex](AssertMex) from  
your help file, e.g. foo.m, asserts the existence of a mex file foo.mex.  
If no such mex file exists then [AssertMex](AssertMex) will exit with an error.  
  
Assert Mex is useful for detecting the error condition when a .m help  
file is mistakenly executed because the correspondig .mex file is  
missing. When foo.mex is missing, MATLAB silently executes the help file  
foo.m instead.  Calling [AssertMex](AssertMex) within foo.m detects and reports that  
error. E.g., in [Screen](Screen).m you'll find [AssertMex](AssertMex)('[Screen](Screen).m') to handle  
missing or dysfunctional [Screen](Screen) mex files properly.  
 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [AssertOpenGL](AssertOpenGL), COMPUTER, [IsOSX](IsOSX), [IsWin](IsWin)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/AssertMex.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/AssertMex.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/AssertMex.m</code>
</div>

