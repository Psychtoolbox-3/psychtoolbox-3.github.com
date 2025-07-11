# [PsychJavaSwingCleanup](PsychJavaSwingCleanup)
##### >[Psychtoolbox](Psychtoolbox)>[PsychJava](PsychJava)

[PsychJavaSwingCleanup](PsychJavaSwingCleanup) - Clean up some internal Java stuff.  
  
The Matlab GUI for releases older than R2025a is based on Java Swing,  
which occasionly causes problems when used with Psychtoolbox due to  
internal quirks of Swing's [RepaintManager](RepaintManager) class ("[OutOfMemoryError](OutOfMemoryError) in  
Java heap space"). [PsychJavaSwingCleanup](PsychJavaSwingCleanup)() forces the [RepaintManager](RepaintManager) to  
re-initialize by temporarily setting its screen buffer to zero size.  
Calling the garbage collector is probably not really necessary because it  
gets called by Matlab at some point anyway. Finally we try to overcome  
the problem that the [RepaintManager](RepaintManager) apparently forgets about its dirty  
regions while re-initializing.  
  
This routine is closely derived from the one posted in Psychtoolbox forum  
message \#16043 by user qx1147.  
  
Another possible solution is described and offered in message \#13975 by  
Davide Tabarelli.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychJava/PsychJavaSwingCleanup.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychJava/PsychJavaSwingCleanup.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychJava/PsychJavaSwingCleanup.m</code>
</div>

