# [PrintStruct](PrintStruct)
##### >[Psychtoolbox](Psychtoolbox)>[PsychAlpha](PsychAlpha)

function [PrintStruct](PrintStruct)(dataStruct, [filePtr], [indentChar], [numIndentSpaces], [numberFormat])  
  
Display the contents of struct arrays to arbitrary nesting depth.  By  
default [PrintStruct](PrintStruct) prints to the MATLAB command window. If a file  
pointer argument is supplied then it prints the contents of the struct  
to a file.    
  
Nested fields within the struct are indented numIndentSpaces for each level  
of nesting.  numIndenSpace is equal to one space.  The indentation character   
by default is the space character.    
  
Pass the empty vector, "[ ]" for either optional argument to specify  
the default.  
  
[PrintStruct](PrintStruct) was suggested by Marialuisa Martelli as a convenient way to   
display experiment parameters and results stored in struct. It's still   
experimental.  The readability of the output could be improved by   
including array indices in the output along with the struct field  names.  
Communicating that by using indentiation and spacing does not work well  
for complicated structures and large arrays.    
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychAlpha/PrintStruct.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychAlpha/PrintStruct.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychAlpha/PrintStruct.m</code>
</div>

