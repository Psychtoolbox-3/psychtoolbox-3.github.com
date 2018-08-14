# [DeEmptify](DeEmptify)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

in = [DeEmptify](DeEmptify)(in,column)  
deletes empty cells or rows from cellarray:  
  
- if only IN is specified, IN has to be a vector. IN will be returned  
  with all empty cells deleted  
- if IN is a matrix, COLUMN must be specified. Rows are only  
  deleted from IN when an empty cell is encountered in a column  
  specified in COLUMN. COLUMN can be a vector  
  
Example:  
  [DeEmptify](DeEmptify)({'','r','','re'})  
  ans =   
      'r'    're'  
  
  a = {'p' 'r'  ''; ...  
       '' 're' 'r'}  
  
  [DeEmptify](DeEmptify)(a,3)  
  ans =   
       ''    're'    'r'  
  
  [DeEmptify](DeEmptify)(a,1)  
  ans =   
       'p'   'r'     ''  
  
  [DeEmptify](DeEmptify)(a,1) or [DeEmptify](DeEmptify)(a,[1 3])  
  ans =   
      Empty cell array: 0-by-3  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/DeEmptify.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/DeEmptify.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/DeEmptify.m</code>
</div>

