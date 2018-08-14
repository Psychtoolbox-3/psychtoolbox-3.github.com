# [FlushCalFile](FlushCalFile)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

[FlushCalFile](FlushCalFile)([filespec],[nKeep])  
  
Flush all but the most recent calibrations in a file.  
  
If no filespec is given, flushes file default.mat.  If  
a an integer is given, flushes file screenN.mat.  If  
a string is given, loads from string.mat.  
  
Argument nKeep specifies how many calibrations to  
keep.  If fewer than nKeep are in the file, all are  
kept.  If nKeep is zero, file is emptied.  nKeep  
defaults to 1.  
  
If specified file cannot be found does nothing.  
  
8/26/97  dhb  Wrote it.  
8/21/00  dhb  Update for dual cal dir scheme.  Not tested hard.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/FlushCalFile.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/FlushCalFile.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/FlushCalFile.m</code>
</div>

