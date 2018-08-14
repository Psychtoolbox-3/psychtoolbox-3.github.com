# [FindRepeatAlongDims](FindRepeatAlongDims)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

find repeated rows or columns in a matrix.  
inds = [FindRepeatAlongDims](FindRepeatAlongDims)(in,dim)  
example:  
in =  
     1     2     3  
     2     3     4  
     4     5     6  
     1     2     3  
     1     2     3  
     4     5     6  
[FindRepeatAlongDims](FindRepeatAlongDims)(in,1)  % check for repeated rows  
ans =   
     5                    % the fifth row is the same as the fourth row,  
                            repeat!  
  
for N-D dimensions, this function can also find repeats along the highest  
dimension, such as finding repeated planes in a 3D matrix.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/FindRepeatAlongDims.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/FindRepeatAlongDims.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/FindRepeatAlongDims.m</code>
</div>

