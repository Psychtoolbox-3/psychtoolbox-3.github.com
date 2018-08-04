# [AddPsychJavaPath](AddPsychJavaPath)
##### >[Psychtoolbox](Psychtoolbox)>[PsychJava](PsychJava)

Add Psychtoolbox directories containing Java classes to the path  
which MATLAB searches for Java classes.  The MATLAB Java path is separate  
from the path searched for .m and mex functions.  
  
[PsychtJavaPaths](PsychtJavaPaths) updates the MATLAB Java path lazily, detecting first  
whether the MATLAB paths have already been changed before making changes.  
  
[AddPsychJavaPath](AddPsychJavaPath) is called by Psychtoolbox functions which depend on  
Psychtoolbox Java classes; It should be unnecessary to use it within your  
own programs.      
  
see also: [PsychJava](PsychJava), [IsPsychJavaPathSet](IsPsychJavaPathSet)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychJava/AddPsychJavaPath.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychJava/AddPsychJavaPath.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychJava/AddPsychJavaPath.m</code>
</div>

