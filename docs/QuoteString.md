# [QuoteString](QuoteString)
##### >[Psychtoolbox](Psychtoolbox)>[PsychFiles](PsychFiles)

string=[QuoteString](QuoteString)(string)  
  
Wraps a string in quotes, after doubling any embedded quotes.  
E.g. "Denis's disk" becomes "'Denis''s disk'"  
This is useful when supplying literal filenames in an eval statement.  
The quoting is necessary because the filename may contain spaces.  
The doubling is necessary because a single quote would be interpreted  
as the end of the string.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychFiles/QuoteString.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychFiles/QuoteString.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychFiles/QuoteString.m</code>
</div>

