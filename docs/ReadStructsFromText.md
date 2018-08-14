# [ReadStructsFromText](ReadStructsFromText)
##### >[Psychtoolbox](Psychtoolbox)>[PsychFiles](PsychFiles)

theStructs = [ReadStructsFromText](ReadStructsFromText)(filename)  
  
Open a tab delimited text file.  The first row should  
contain the field names for a structure.  Each following  
row contains the data for one instance of that structure.  
  
This routine reads each row and returns an array of structures,  
one struct for each row, with the data filled in.  Data  
can be numeric or string for each field.  
  
Not a lot of checking is done for cases where the read file  
fails to conform to the necessary format.  
  
See Also: [WriteStructsToText](WriteStructsToText)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychFiles/ReadStructsFromText.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychFiles/ReadStructsFromText.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychFiles/ReadStructsFromText.m</code>
</div>

