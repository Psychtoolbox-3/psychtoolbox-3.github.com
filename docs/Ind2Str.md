# [Ind2Str](Ind2Str)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

str = [Ind2Str](Ind2Str)(p)  
converts indices (numbers) to characters (base 10 to base 26 conversion):  
[Ind2Str](Ind2Str)( 1) = 'a'  
[Ind2Str](Ind2Str)(26) = 'z'  
[Ind2Str](Ind2Str)(27) = 'ba'  
if P is a vector or matrix of indices, output will be a cell of the  
same dimensions  
representation with least number of characters necessary is used  
  
str = [Ind2Str](Ind2Str)(p,numchar)  
representation of at least NUMCHAR length will be used for output:  
[Ind2Str](Ind2Str)([1,34,45],3) = {'aab','abi','abt'}  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/Ind2Str.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/Ind2Str.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/Ind2Str.m</code>
</div>

