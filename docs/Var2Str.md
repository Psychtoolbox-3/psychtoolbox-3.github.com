# [Var2Str](Var2Str)
##### >[Psychtoolbox](Psychtoolbox)>[PsychFiles](PsychFiles)

str = [Var2Str](Var2Str)(in,name)  
  
Takes variable IN and creates a string representation of it that would  
return the original variable when fed to eval(). NAME is the name of the variable  
that will be printed in this string.  
Can process any (combination of) MATLAB built-in datatype  
  
examples:  
  [Var2Str](Var2Str)({4,7,'test',@exp})  
  ans =  
      {4,7,'test',@exp}  
  
  var.field1.field2 = {logical(1),'yar',int32(43),[3 6 1 2],@isempty};  
  [Var2Str](Var2Str)(var,'var2')  
  ans =  
      var2.field1.field2 = {true,'yar',int32(43),[3,6,1,2],@isempty};  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychFiles/Var2Str.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychFiles/Var2Str.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychFiles/Var2Str.m</code>
</div>

