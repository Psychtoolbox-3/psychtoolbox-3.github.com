# [IsACell](IsACell)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

bool = [IsACell](IsACell)(input,fhndl)  
  
checks if there is any element in the cell INPUT that satisfies the  
logical condition in function FHNDL  
works recursively: cells in cells (etc) also checked  
the function FHNDL must return a scalar  
  
examples:  
checks if there is any struct in the cell:  
fhndl = @isstruct  
check if there is any element in the cell extending  
over more than 2 dimensions:  
fhndl = @(x)ndims(x)\>2  
  
DN    2008-05-28  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/IsACell.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/IsACell.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/IsACell.m</code>
</div>

