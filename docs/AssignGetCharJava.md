# [AssignGetCharJava](AssignGetCharJava)
##### >[Psychtoolbox](Psychtoolbox)>[PsychJava](PsychJava)

[AssignGetCharJava](AssignGetCharJava) - Helper function for Java based [GetChar](GetChar).  
  
This routine is called during initialization from [ListenChar](ListenChar),  
[CharAvail](CharAvail), [GetChar](GetChar) and [FlushEvents](FlushEvents). It tries as hard as possible  
instantiate a Java object of the [GetCharJava](GetCharJava) class and returns it  
if successfull. Different versions of Matlab use different versions  
of the Java virtual machine. Matlab can only load versions of  
[GetCharJava](GetCharJava).class that were compiled with the same Java version as  
the one that Matlab uses. Therefore we provide multiple versions of  
the [GetCharJava](GetCharJava).class, each compiled against a different Java version.  
We try to instantiate the newest version. If that fails, we try the  
2nd newest version, and so on. If all versions bundled with PTB failed  
to instantiate, the behaviour depends on the availability of an installed  
Java compiler. If a "javac" compiler is available, as on [MacOS](MacOS)-X, we invoke  
it on the source code to built a customized version of [GetCharJava](GetCharJava) for that  
machine. Otherwise we give up and fail.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychJava/AssignGetCharJava.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychJava/AssignGetCharJava.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychJava/AssignGetCharJava.m</code>
</div>

