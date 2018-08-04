# [Replace](Replace)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

[Replace](Replace) - [Replace](Replace) Elements  
  B = [Replace](Replace)(A,S1,S2) returns a matrix B in which the elements in A that   
  are in S1 are Replaced by those in S2. In general, S1 and S2 should have  
  an equal number of elements. If S2 has one element, it is expanded to  
  match the size of S1. Examples:  
     [Replace](Replace)([1 1 2 3 4 4],[1 3],[0 99]) % -\>  [ 0 0 2 99 4 4]  
     [Replace](Replace)(1:10,[3 5 6 8],[NaN)](NaN)) % -\>  [ 1 2 [NaN](NaN) 4 [NaN](NaN) [NaN](NaN) 7 [NaN](NaN) 9 10]  
     [Replace](Replace)([1 [NaN](NaN) Inf 8 99],[[NaN](NaN) Inf 99],[12 13 14]) % -\> [1 12 13 8 14]  
  
  [B, TF] = [Replace](Replace)(A,S1,S2) also returns a logical vector TF of the same  
  size as A. TF is true for those elements that are replaced.  
  
  A and S1 can be cell arrays of strings. In that case S2 should be a  
  cell array as well but can contain mixed types. Example:  
     [Replace](Replace)({'aa' 'b' 'c' 'a'},{'a' 'b'}, {'xx' 2}) %-\> {'aa' [2] 'c' 'xx'}  
  
  If S2 is empty, the elements of A that are in S1  
  are removed. Examples:  
     [Replace](Replace)(1:5,[2 4],[]) % -\> [1 3 5]  
     [Replace](Replace)({'aa' 'a' 'b' 'aa' 'c'},{'aa','c'},{}) % -\> {'a', 'b'}  
  
  See also FIND, STRREP, REGEXPREP, ISMEMBER  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/Replace.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/Replace.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/Replace.m</code>
</div>

