# [WriteStructsToText](WriteStructsToText)
##### >[Psychtoolbox](Psychtoolbox)>[PsychFiles](PsychFiles)

[WriteStructsToText](WriteStructsToText)(filename,theStructs)  
  
Write a tab delimited text file.  The first row should  
contain the field names for a structure.  Each following  
row contains the data for one instance of that structure.  
  
This routine writes each element of the structure array as a row.  
Only numeric and string field values are supported.  
  
If the filename is a string, this routine handles opening and  
closing of the file.  Otherwise, this routine assumes  
that what was passed is a valid fid and uses it as such,  
leaving the calling routine to do the opening and closing.  
  
06/16/03 dhb  Wrote it.  
07/01/03 dhb  Support string fields too.  
08/12/06 dhb  Call filetype only if OS9.  
07/07/13 dhb  Add handling of non-string filename as fid.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychFiles/WriteStructsToText.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychFiles/WriteStructsToText.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychFiles/WriteStructsToText.m</code>
</div>

